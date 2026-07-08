<template>
    <main class="mx-auto max-w-4xl px-6 py-10 text-white">
        <section class="mb-8">
            <p class="mb-2 font-semibold text-cyan-400">
                {{ courseTitle }}
            </p>
            <h1 class="mb-3 text-4xl font-bold">
                {{ assessmentTitle }}
            </h1>

            <p v-for="instruction in instructions" :key="instruction" class="mb-2 text-slate-300">
                {{ instruction }}
            </p>
        </section>

        <section v-if="!quizFinished" class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
            <div v-if="!hasAnswered" class="mb-4 flex items-center justify-between">
                <p class="text-sm text-slate-400">
                    Question {{ currentQuestionIndex + 1 }} of {{ questionLimit }}
                </p>

                <p class="text-sm text-slate-400">
                    Score: {{ score }}
                </p>
            </div>

            <div v-if="!hasAnswered" class="rounded-xl border border-slate-700 bg-slate-950 p-5">
                <p class="mb-2 text-sm text-slate-400">
                    {{ currentQuestion?.questionText }}
                </p>
            </div>

            <div v-if="!hasAnswered" class="mt-6 flex flex-col gap-3">
                <button
                    v-for="choice in currentChoices"
                    :key="choice"
                    class="rounded-xl bg-slate-500 px-5 py-3 font-medium text-white transition hover:bg-slate-400"
                    @click="answerQuestion(choice)"
                >
                    {{ choice }}
                </button>
            </div>

            <div
                v-else
                class="mt-6 rounded-xl border p-5"
                :class="isCorrect ? 'border-emerald-500 bg-emerald-950/40' : 'border-red-500 bg-red-950/40'"
            >
                <p v-if="!isCorrect" class="mb-2 text-lg text-slate-300">
                    You answered: <strong>{{ selectedAnswer }}</strong>
                </p>

                <p class="mb-2 text-lg text-slate-300">
                    Correct answer: <strong>{{ currentQuestion?.correctAnswer }}</strong>
                </p>

                <p class="mb-4 text-sm text-slate-300">
                    {{ currentQuestion?.explanation }}
                </p>

                <button
                    class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400"
                    @click="nextQuestion"
                >
                    {{ isLastQuestion ? 'Finish quiz' : 'Next question' }}
                </button>
            </div>
        </section>

        <section v-if="quizFinished" class="mt-6 rounded-2xl border border-slate-800 bg-slate-900 p-6">
            <h2 class="mb-2 text-2xl font-bold">
                Quiz complete
            </h2>

            <p class="text-slate-300">
                You scored {{ score }} out of {{ questionLimit }}.
            </p>

            <p v-if="hasPassed" class="text-slate-300">
                Congratulations! You passed.
            </p>
            <p v-else class="text-slate-300">
                You didn't score {{ passPercentageLabel }} on the assessment.
            </p>

            <button
                class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400"
                @click="restartQuiz"
            >
                Try again
            </button>
        </section>
    </main>
</template>

<script setup lang="ts">
import type { AssessmentQuestion } from '~/types/assessment'

const props = withDefaults(defineProps<{
    courseTitle: string
    assessmentTitle: string
    instructions: string[]
    questions: AssessmentQuestion[]
    maxQuestions?: number
    passPercentage?: number
}>(), {
    maxQuestions: undefined,
    passPercentage: 0.7,
})

const questionLimit = computed(() => {
    return Math.min(props.maxQuestions ?? props.questions.length, props.questions.length)
})
const minCorrectAnswers = computed(() => Math.ceil(questionLimit.value * props.passPercentage))
const passPercentageLabel = computed(() => `${Math.round(props.passPercentage * 100)}%`)

const currentQuestionIndex = ref(0)
const selectedAnswer = ref<string | null>(null)
const score = ref(0)
const quizFinished = ref(false)
const shuffledQuestions = ref<AssessmentQuestion[]>(shuffleQuestions())

const currentQuestion = computed(() => shuffledQuestions.value[currentQuestionIndex.value])
const currentChoices = computed(() => shuffleArray(currentQuestion.value?.choices ?? []))
const hasAnswered = computed(() => selectedAnswer.value !== null)
const hasPassed = computed(() => score.value >= minCorrectAnswers.value)
const isCorrect = computed(() => selectedAnswer.value === currentQuestion.value?.correctAnswer)
const isLastQuestion = computed(() => currentQuestionIndex.value === questionLimit.value - 1)

function shuffleArray<T>(items: T[]) {
    return [...items].sort(() => Math.random() - 0.5)
}

function shuffleQuestions() {
    return shuffleArray(props.questions).slice(0, questionLimit.value)
}

function answerQuestion(answer: string) {
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
    shuffledQuestions.value = shuffleQuestions()
}
</script>
