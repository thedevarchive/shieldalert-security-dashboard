<template>
  <main class="mx-auto max-w-4xl px-6 py-10 text-white">
    <section class="mb-8">
      <h1 class="mb-3 text-4xl font-bold">
        Phishing Email Quiz
      </h1>

      <p class="text-slate-300">
        Read each email and decide whether it looks safe or suspicious.
      </p>
    </section>

    <section class="rounded-2xl border border-slate-800 bg-slate-900 p-6" v-if="!quizFinished">
      <div class="mb-4 flex items-center justify-between" v-if="!hasAnswered">
        <p class="text-sm text-slate-400">
          Question {{ currentQuestionIndex + 1 }} of {{ questions.length }}
        </p>

        <p class="text-sm text-slate-400">
          Score: {{ score }}/{{ questions.length }}
        </p>
      </div>

      <!-- Format questions like an email -->
      <div class="rounded-xl border border-slate-700 bg-slate-950 p-5" v-if="!hasAnswered">
        <p class="mb-2 text-sm text-slate-400">
          From: {{ currentQuestion?.from }}
        </p>

        <p class="mb-4 text-lg font-semibold">
          {{ currentQuestion?.subject }}
        </p>

        <p class="whitespace-pre-line text-slate-300">
          {{ currentQuestion?.body }}
        </p>
      </div>
      
      <!-- User choices -->
      <div v-if="!hasAnswered" class="mt-6 flex gap-3">
        <button @click="answerQuestion('safe')"
          class="rounded-xl bg-emerald-500 px-5 py-3 font-medium text-white transition hover:bg-emerald-400">
          Looks safe
        </button>

        <button @click="answerQuestion('phishing')"
          class="rounded-xl bg-red-500 px-5 py-3 font-medium text-white transition hover:bg-red-400">
          Looks suspicious
        </button>
      </div>

      <div v-else class="mt-6 rounded-xl border p-5"
        :class="isCorrect ? 'border-emerald-500 bg-emerald-950/40' : 'border-red-500 bg-red-950/40'">
        <p class="mb-2 text-lg font-semibold">
          {{ isCorrect ? 'Correct' : 'Not quite' }}
        </p>

        <p class="mb-4 text-sm text-slate-300">
          {{ currentQuestion?.explanation }}
        </p>

        <div>
          <p class="mb-2 text-sm font-medium text-slate-200">
            Red flags:
          </p>

          <ul class="list-inside list-disc space-y-1 text-sm text-slate-300">
            <li v-for="flag in currentQuestion?.redFlags" :key="flag">
              {{ flag }}
            </li>
          </ul>
        </div>

        <!-- This button moves user to the next question -->
        <button @click="nextQuestion"
          class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400">
          {{ isLastQuestion ? 'Finish quiz' : 'Next question' }}
        </button>
      </div>
    </section>

    <section v-if="quizFinished" class="mt-6 rounded-2xl border border-slate-800 bg-slate-900 p-6">
      <h2 class="mb-2 text-2xl font-bold">
        Quiz complete
      </h2>

      <p class="text-slate-300">
        You scored {{ score }} out of {{ questions.length }}.
      </p>

      <!-- Button for resetting quiz -->
      <button @click="restartQuiz"
        class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400">
        Try again
      </button>
    </section>
  </main>
</template>

<script setup lang="ts">
useHead({
  title: 'Phishing Email Quiz',
})

type Answer = 'safe' | 'phishing'

//from, subject and body simulate a sample email question
//correctAnswer determines if email is phishing or not 
//explanation and redFlags explain to user why email is phishing or not 
type Question = {
  from: string
  subject: string
  body: string
  correctAnswer: Answer
  explanation: string
  redFlags: string[]
}

//list of questions
let questions: Question[] = [
  {
    from: 'skay@funds.biz',
    subject: '[ACTION REQUIRED] Last day to Claim Funds',
    body: `Hello!!!!

I am here to inform you on this month August 29th is last day you have to receive your fund and i am here to tell you that this fund is $3.9 million in an atm card that is with us has over stayed and the Government of this country has notify us to return this atm card or they empty the fund in the card to the Federal Government account. 

They have made it known to us today that if you fail to send the fees today that this fund will no more be your fund. I advise you not to allow that to happen. You have from now to midnight today to send it or this fund will be out of your name. It is not needed tomorrow but today sending service then buy an Apple Card and send it here now. 

Best regards, 
Susan`,
    correctAnswer: 'phishing',
    explanation:
      'This email creates urgency and tricks the user into buying gift cards in exchange for a large sum of money.',
    redFlags: [
      'Urgent language',
      'Suspicious sender domain',
      'Poor grammar and punctuation',
      'Unrealistic financial claim',
      'Vague government threats',
      'Unsolicited money offer',
    ],
  },
  {
    from: 'admin@paypayx.com',
    subject: 'Update Your Account Information! Your PayPal ID has been locked for security reasons',
    body: `Dear Client, 

Your PayPal Account has been locked for security reasons.
Your account appears to be out of date and needs to update account ownership information, so that we can protect your account and improve our service to maintain your privacy.

To continue using your account, we recommend that you update your information 24 hours ago or your account will be permanently locked. 

Verification account now: https://paypyp.com/verify

Sincerely, 
PayPal Support`,
    correctAnswer: 'phishing',
    explanation:
      'This email creates urgency and sends the user to a suspicious domain that does not clearly match the real company domain.',
    redFlags: [
      'Urgent language',
      'Suspicious sender domain',
      'Poor grammar',
      'Threat of permanent account lock',
      'External link pretending to be an internal page'
    ],
  },
  {
    from: 'noreply@touyoube.com',
    subject: 'Copyright Strike Notice',
    body: `Hi,

Due to a copyright takedown notice that we received, we have taken down one of your videos. This means that your video can no longer be played, and you may have lost access to some features on your account. Getting multiple copyright strikes can lead to the termination of your account and the removal of all your videos.

Why this can happen: 
- One or more of your videos contained copyrighted content 
- Copyright owners can choose to take down videos that contain their content 

View details: https://yt-youtube.com/details

Sincerely
YT Creator Award Team`,
    correctAnswer: 'phishing',
    explanation:
      'This email creates urgency and sends the user to a suspicious domain that does not clearly match the real company domain.',
    redFlags: [
      'Urgent language',
      'Suspicious sender domain',
      'External link pretending to be an internal page',
      'Signature at the bottom does not match expected department/team',
    ],
  },
  {
    from: 'hello@clockup.net',
    subject: 'Sponsorship T&C',
    body: `Be sure to read this text for further cooperation 

We are happy to greet you! If you are reading this, then most likely you want to work with us. This is the right choice! If you enjoy working with us, we can do it on an ongoing basis.

You can download the program and create an affiliate link on our website. 
To download our program, go to our website: https://clockup.net 
and after scrolling through the site to the very end, click the "Download" button. After that, you need to enter our promo code. 
Your personal promo code: ImHAt11 

Sincerely
Clockup Team`,
    correctAnswer: 'phishing',
    explanation:
      'This email sends the user to a suspicious domain and asks the user to download software.',
    redFlags: [
      'Poor grammar',
      'Verbose phrasing and repetitive sentences',
      'No clear explanation of company/product',
      'Unsolicited partnership offer',
    ],
  },
  {
    from: 'johnsmith@icloud.io',
    subject: 'Storage Limit reached',
    body: `Dear customer, 

Your iCloud storage is full . 

But, as part of your loyalty program, you can now receive an additional 50GB for free before the files on your iCloud drive are deleted.

RECEIVE 50 GB: https://lcloud.com/free50/AbDx9357`,
    correctAnswer: 'phishing',
    explanation:
      'This email creates urgency and sends the user to a suspicious domain that does not clearly match the real company domain.',
    redFlags: [
      'Urgent language',
      'Suspicious sender domain',
      'Bad punctuation',
      'Tries to reward urgency with a "loyalty program"', 
      'Threat of permanent deletion',
    ],
  },
  {
    from: 'noreply@cba.com.au',
    subject: 'Avoid Vishing Scammers',
    body: `Vishing scams have become more rampant and convincing. How can you protect yourself against this?

- Never give your OTP to anyone for any reason. By giving your OTP out, you put your account at great risk.
- Don’t fall for confident voices on the other line. Fraudsters will do anything to get your confidential information and will use it to access your bank accounts and perform unauthorised transactions.
- Be wary of the urgency. When receiving calls that require immediate attention from unknown numbers, be extra cautious as you might be talking to a vishing scammer. 
- Keep yourself informed of new schemes. Vishing may be on the rise, but that does not mean phishing, social engineering and other fraud schemes are gone. Stay informed by reading your bank’s advisories.

Reminder: CommBank will never ask for your credentials via call, text or email.`,
    correctAnswer: 'safe',
    explanation:
      'This looks like a normal banking email informing the client of potential scams.',
    redFlags: ['No major red flags'],
  },
  {
    from: 'no-reply@c.anz.com',
    subject: 'Something not right? Take control in the ANZ App',
    body: `Hi, 

Something not right? Take control instantly by blocking your card and reporting suspicious transactions in the ANZ App, available 24/7.

If you see a transaction you don't recognise:

1. Tap on a transaction 
2. Tap Something not right? 
3. Follow the prompts (you can add more than one transaction if you need to)
4. We'll take care of the rest 

Don't see Something not right? Simply tap Support and Message Us.`,
    correctAnswer: 'safe',
    explanation:
      'This looks like a normal banking email informing the client of what to do when they see suspicious transactions on their account.',
    redFlags: ['No major red flags'],
  },
  {
    from: 'it-support@company-security-login.com',
    subject: 'Urgent: Password expires today',
    body: `Hello,

Your work password will expire today. To avoid losing access, confirm your login details immediately using the link below:

https://company-security-login.com/verify

IT Support`,
    correctAnswer: 'phishing',
    explanation:
      'This email creates urgency and sends the user to a suspicious domain that does not clearly match the real company domain.',
    redFlags: [
      'Urgent language',
      'Suspicious sender domain',
      'Asks user to confirm login details',
      'External link pretending to be an internal page',
    ],
  },
  {
    from: 'newsletter@securityweekly.com',
    subject: 'Your weekly security tips',
    body: `Hi,

Here are this week's security awareness tips:
- Use unique passwords
- Enable multi-factor authentication
- Check links before clicking

Thanks for subscribing.`,
    correctAnswer: 'safe',
    explanation:
      'This looks like a normal newsletter. It does not ask for credentials, payment, urgent action, or sensitive information.',
    redFlags: ['No major red flags'],
  },
  {
    from: 'payroll@cornpany.com',
    subject: 'Action required: Salary payment failed',
    body: `Hi,

Your salary payment failed because your bank details are outdated.

Please reply with your account number and BSB so payroll can process your payment today.

Payroll Team`,
    correctAnswer: 'phishing',
    explanation:
      'This email asks for sensitive banking information and uses a domain that may be impersonating “company.com”.',
    redFlags: [
      'Asks for banking details by email',
      'Creates financial pressure',
      'Suspicious misspelled domain',
      'Requests sensitive personal information',
    ],
  },
]

//shuffle questions 
const shuffledQuestions = [...questions].sort(() => Math.random() - 0.5)
questions = shuffledQuestions

const currentQuestionIndex = ref(0) // get current question number
const selectedAnswer = ref<Answer | null>(null) // gets user's answer 
const score = ref(0) // get user's score 
const quizFinished = ref(false) //check if quiz is finished

const currentQuestion = computed(() => questions[currentQuestionIndex.value]) //get current question

const hasAnswered = computed(() => selectedAnswer.value !== null) //check if user has answered 

//compares user's answers to correct answer of current question
const isCorrect = computed(() => {
  return selectedAnswer.value === currentQuestion.value?.correctAnswer
})

//checks if user is at last question to finish the quiz
const isLastQuestion = computed(() => {
  return currentQuestionIndex.value === questions.length - 1
})

//record user's answer and add 1 to user's score if user got it right 
function answerQuestion(answer: Answer) {
  selectedAnswer.value = answer

  if (answer === currentQuestion.value?.correctAnswer) {
    score.value++
  }
}

//increment quiz question index by 1 unless quiz is at last question 
//after moving to next question, reset user's selected answer to null 
function nextQuestion() {
  if (isLastQuestion.value) {
    quizFinished.value = true
    return
  }

  currentQuestionIndex.value++
  selectedAnswer.value = null
}

//reset all values and allow user to take the quiz again 
function restartQuiz() {
  currentQuestionIndex.value = 0
  selectedAnswer.value = null
  score.value = 0
  quizFinished.value = false
}
</script>
