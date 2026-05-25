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

      <div v-if="!hasAnswered" class="mt-6 flex gap-3">
        <button
          @click="answerQuestion('safe')"
          class="rounded-xl bg-emerald-500 px-5 py-3 font-medium text-white transition hover:bg-emerald-400"
        >
          Looks safe
        </button>

        <button
          @click="answerQuestion('phishing')"
          class="rounded-xl bg-red-500 px-5 py-3 font-medium text-white transition hover:bg-red-400"
        >
          Looks suspicious
        </button>
      </div>

      <div
        v-else
        class="mt-6 rounded-xl border p-5"
        :class="isCorrect ? 'border-emerald-500 bg-emerald-950/40' : 'border-red-500 bg-red-950/40'"
      >
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

        <button
          @click="nextQuestion"
          class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400"
        >
          {{ isLastQuestion ? 'Finish quiz' : 'Next question' }}
        </button>
      </div>
    </section>

    <section
      v-if="quizFinished"
      class="mt-6 rounded-2xl border border-slate-800 bg-slate-900 p-6"
    >
      <h2 class="mb-2 text-2xl font-bold">
        Quiz complete
      </h2>

      <p class="text-slate-300">
        You scored {{ score }} out of {{ questions.length }}.
      </p>

      <button
        @click="restartQuiz"
        class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400"
      >
        Try again
      </button>
    </section>
  </main>
</template>

<script setup lang="ts">
type Answer = 'safe' | 'phishing'

type Question = {
  from: string
  subject: string
  body: string
  correctAnswer: Answer
  explanation: string
  redFlags: string[]
}

const questions: Question[] = [
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
      'External link pretending to be an internal login page',
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

const currentQuestionIndex = ref(0)
const selectedAnswer = ref<Answer | null>(null)
const score = ref(0)
const quizFinished = ref(false)

const currentQuestion = computed(() => questions[currentQuestionIndex.value])

const hasAnswered = computed(() => selectedAnswer.value !== null)

const isCorrect = computed(() => {
  return selectedAnswer.value === currentQuestion.value?.correctAnswer
})

const isLastQuestion = computed(() => {
  return currentQuestionIndex.value === questions.length - 1
})

function answerQuestion(answer: Answer) {
  selectedAnswer.value = answer

  if (answer === currentQuestion.value?.correctAnswer) {
    score.value++
  }
}

function nextQuestion() {
  if (isLastQuestion.value) {
    quizFinished.value = true
    return
  }

  currentQuestionIndex.value++
  selectedAnswer.value = null
}

function restartQuiz() {
  currentQuestionIndex.value = 0
  selectedAnswer.value = null
  score.value = 0
  quizFinished.value = false
}
</script>