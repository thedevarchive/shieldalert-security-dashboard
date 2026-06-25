<template>
    <main class="mx-auto max-w-4xl px-6 py-10 text-white">
        <section class="mb-8">
            <p class="mb-2 font-semibold text-cyan-400">
                Information Security Management
            </p>
            <h1 class="mb-3 text-4xl font-bold">
                Midpoint Assessment
            </h1>

            <p class="mb-2 text-slate-300">
                Read each question carefully and select the best answer from the provided options.
            </p>
            <p class="mb-2 text-slate-300">
                The test will take about 30 minutes to complete.
            </p>
            <p class="mb-2 text-slate-300">
                You must score 70% to pass the test.
            </p>
        </section>

        <section class="rounded-2xl border border-slate-800 bg-slate-900 p-6" v-if="!quizFinished">
            <div class="mb-4 flex items-center justify-between" v-if="!hasAnswered">
                <p class="text-sm text-slate-400">
                    Question {{ currentQuestionIndex + 1 }} of {{ maxQuestions }}
                </p>

                <p class="text-sm text-slate-400">
                    Score: {{ score }}/{{ questions.length }}
                </p>
            </div>

            <div class="rounded-xl border border-slate-700 bg-slate-950 p-5" v-if="!hasAnswered">
                <p class="mb-2 text-sm text-slate-400">
                    {{ currentQuestion?.questionText }}
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
//questionText contains the question 
//correctAnswer has the correct answer among the choices
//explanation has the justification for the correct answer
type Question = {
    questionText: string
    choices: string[]
    correctAnswer: string
    explanation: string
}

// First 12 questions: Module 1
// Next ? questions: Module 2
// Next ? questions: Module 3
// Next ? questions: Module 4
// Next ? questions: Module 5
// Last ? questions: Module 6
let questions: Question[] = [
    {
        questionText: "Why is information security essential?",
        choices: [
            "Information has certain characteristics, that when violated, becomes no longer useful.",
            "It allows information to be shared freely without restriction.",
            "It guarantees that cyberattacks can never harm an organisation.",
            "It ensures that all employees have access to company information at all times.",
        ],
        correctAnswer: "Information has certain characteristics, that when violated, becomes no longer useful.",
        explanation: "Information has three properties: confidentiality, integrity and availability. When any of these are violated, the information becomes exposed to unintended users who could make the information unreliable and less accessible to the users who have the right to access it."
    },
    {
        questionText: "In cybersecurity, what does the letters in CIA stand for?",
        choices: [
            "Central, Intellligence, Agency",
            "Curiosity, Ingenuity, Advocacy",
            "Customisability, Identification, Accountability",
            "Confidentiality, Integrity, Availability",
        ],
        correctAnswer: "Confidentiality, Integrity, Accessbility",
        explanation: "CIA stands for confidentiality, integrity and accessbility, which are also the three properties of reliable information."
    },
    {
        questionText: "Which of these is NOT an additional goal for establishing security?",
        choices: ["Avalability", "Authentication", "Accountability", "Authorisation"],
        correctAnswer: "Availability",
        explanation: "Availability is a necessary security goal. Authentication, accountability and authorisation are considered additional security goals."
    },
    {
        questionText: "Which of these additional security goals refers to the ability to recognise users who can access the information?",
        choices: ["Identification", "Authentication", "Authorisation", "Non-repudiation"],
        correctAnswer: "Identification",
        explanation: "Identification is the additional security goal that refers to the system's ability to recognise users and who has rightful access to the information."
    },
    {
        questionText: "Which of these additional security goals refers to the ability of the system to create irrefutable proof that a user has done a certain activity to the information?",
        choices: ["Identification", "Accountability", "Authorisation", "Non-repudiation"],
        correctAnswer: "Non-repudiation",
        explanation: "Non-repudiation refers to creating irrefutable proof that the activity occurred and the user has done it."
    },
    {
        questionText: "A law student hacked into the university's system to change their marks. In this situation, which security goal is compromised?",
        choices: ["Confidentiality", "Integrity", "Availability", "None"],
        correctAnswer: "Integrity",
        explanation: "Integrity refers to preventing the modification of information, and since the student modified their marks to make them seem like they have better grades, integrity is violated."
    },
    {
        questionText: "A file that contained personal information and medical details of blood donors was posted on a public website. Which security goal was violated as a result?",
        choices: ["Confidentiality", "Integrity", "Availability", "All three"],
        correctAnswer: "Confidentiality",
        explanation: "As information is disclosed to other users when the file containing personal details is published, confidentiality was compromised."
    },
    {
        questionText: "Due to an outage, payment systems at self-service checkouts in grocery stores were unable to be used. Because of this, which security goal was violated?",
        choices: ["Confidentiality", "Integrity", "Availability", "Authorisation"],
        correctAnswer: "Availability",
        explanation: "Because payment systems were not available for use due to the outage, the availability of those systems were tampered with."
    },
    {
        questionText: "Why is information security essential?",
        choices: [],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "Why is information security essential?",
        choices: [],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "Why is information security essential?",
        choices: [],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "Why is information security essential?",
        choices: [],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [],
        correctAnswer: "",
        explanation: ""
    },
]

//TODO: adjust question limit and pass percentage
const maxQuestions = 10
const passPercentage = 0.7
const minCorrectAnswers = Math.round(maxQuestions * passPercentage)

//shuffle questions 
const shuffledQuestions = [...questions].sort(() => Math.random() - 0.5)
questions = shuffledQuestions

const currentQuestionIndex = ref(0) // get current question number
const selectedAnswer = ref<string | null>(null) // gets user's answer 
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
    return maxQuestions === questions.length - 1
})

//record user's answer and add 1 to user's score if user got it right 
function answerQuestion(answer: string) {
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