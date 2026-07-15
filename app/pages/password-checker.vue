<script setup lang="ts">
import { Eye, EyeOff } from '@lucide/vue'
import TipCard from '~/components/TipCard.vue'

useHead({
  title: 'Password Strength Checker',
})

const password = ref('') //state for password input
const showPassword = ref(false) //determines if inputted password is shown or hidden
const obviousPattern =
  /(p[a4@]ssw[o0]rd|asdf|abc|qwerty|test|testing|welcome|123|1234|1111|0000)/i
const hasObviousPattern = computed(() => obviousPattern.test(password.value))

// label has the password requirements user should ideally follow
// passed contains the boolean condition/regex that checks if user's password is following the requirement
const checks = computed(() => [
  {
    label: 'At least 12 characters long',
    passed: password.value.length >= 12,
  },
  {
    label: 'Contains uppercase letters',
    passed: /[A-Z]/.test(password.value),
  },
  {
    label: 'Contains lowercase letters',
    passed: /[a-z]/.test(password.value),
  },
  {
    label: 'Contains numbers',
    passed: /\d/.test(password.value),
  },
  {
    label: 'Contains special characters',
    passed: /[^A-Za-z0-9]/.test(password.value),
  },
  {
    label: 'Does not contain obvious words',
    passed: !hasObviousPattern.value,
  },
])

//get the number of passed conditions fulfilled by password
const passedChecks = computed(() => {
  return checks.value.filter((check) => check.passed).length
})

//calculate progress bar value
const score = computed(() => {
  if (!password.value) return 0

  const baseScore = Math.round((passedChecks.value / checks.value.length) * 100)

  // keep score at 30 when obvious words are used in the password
  if (hasObviousPattern.value) return Math.min(baseScore, 30)

  return baseScore
})

//display strength of password based on the progress bar value
const strengthLabel = computed(() => {
  if (score.value === 0) return 'Not tested'
  if (score.value < 35) return 'Weak'
  if (score.value < 70) return 'Moderate'
  if (score.value < 90) return 'Strong'
  return 'Very strong'
})

const strengthBarClass = computed(() => {
  if (score.value < 35) return 'bg-red-500'
  if (score.value < 70) return 'bg-yellow-400'
  if (score.value < 90) return 'bg-cyan-400'
  return 'bg-emerald-400'
})

const strengthTextClass = computed(() => {
  if (score.value < 35) return 'text-red-400'
  if (score.value < 70) return 'text-yellow-400'
  if (score.value < 90) return 'text-cyan-400'
  return 'text-emerald-400'
})

const characterSetSize = computed(() => {
  let size = 0

  //get sum of number of possible combinations based on each individual character in password
  if (/[a-z]/.test(password.value)) size += 26 //check for lowercase
  if (/[A-Z]/.test(password.value)) size += 26 //check for uppercase
  if (/\d/.test(password.value)) size += 10 //check for numbers
  if (/[^A-Za-z0-9]/.test(password.value)) size += 32 //check for special characters

  return size
})

const possibleCombinations = computed(() => {
  if (!password.value || characterSetSize.value === 0) return 0

  return characterSetSize.value ** password.value.length
})

const crackTimeSeconds = computed(() => {
  const guessesPerSecond = 1_000_000_000

  // if possible combinations has no value, return 0
  // if an obvious password pattern is detected, also return 0 so that user is informed that this is an easily guessable password
  if (!possibleCombinations.value || hasObviousPattern.value) return 0
  return possibleCombinations.value / guessesPerSecond
})

const crackTimeLabel = computed(() => {
  const seconds = crackTimeSeconds.value

  if (!password.value) return 'Not tested'
  if (seconds < 1) return 'Instantly'
  if (seconds < 60) return `${Math.round(seconds)} seconds`
  if (seconds < 3600) return `${Math.round(seconds / 60)} minutes`
  if (seconds < 86400) return `${Math.round(seconds / 3600)} hours`
  if (seconds < 31536000) return `${Math.round(seconds / 86400)} days`
  if (seconds < 3153600000) return `${Math.round(seconds / 31536000)} years`

  return 'Centuries or more'
})
</script>

<template>
  <main class="mx-auto max-w-4xl px-6 py-10 text-white">
    <section class="mb-8">
      <h1 class="mb-3 text-4xl font-bold">Password Strength Checker</h1>

      <p class="text-slate-300">
        Test how strong a password is based on length, variety and guessability.
      </p>
    </section>

    <section class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
      <label
        for="password"
        class="mb-2 block text-sm font-medium text-slate-300"
      >
        Enter a password
      </label>

      <div class="relative">
        <input
          id="password"
          v-model="password"
          :type="showPassword ? 'text' : 'password'"
          placeholder="Type a password..."
          class="w-full rounded-xl border border-slate-700 bg-slate-950 px-4 py-3 pr-12 text-white outline-none focus:border-cyan-400"
        />

        <button
          type="button"
          @click="showPassword = !showPassword"
          class="absolute right-3 top-1/2 -translate-y-1/2 text-slate-400 transition hover:text-white"
        >
          <Eye v-if="!showPassword" class="h-5 w-5" />
          <EyeOff v-else class="h-5 w-5" />
        </button>
      </div>

      <div class="mt-6">
        <div class="mb-2 flex items-center justify-between">
          <span class="text-sm text-slate-300">Strength</span>
          <span :class="strengthTextClass" class="text-sm font-semibold">
            {{ strengthLabel }}
          </span>
        </div>

        <div class="h-3 rounded-full bg-slate-800">
          <div
            class="h-3 rounded-full transition-all"
            :class="strengthBarClass"
            :style="{ width: `${score}%` }"
          />
        </div>
      </div>

      <ul class="mt-6 space-y-3">
        <li
          v-for="check in checks"
          :key="check.label"
          class="flex items-center gap-3 text-sm"
        >
          <span
            class="flex h-5 w-5 items-center justify-center rounded-full text-xs"
            :class="
              check.passed
                ? 'bg-emerald-500 text-white'
                : 'bg-slate-700 text-slate-300'
            "
          >
            {{ check.passed ? '✓' : '×' }}
          </span>

          <span :class="check.passed ? 'text-slate-200' : 'text-slate-400'">
            {{ check.label }}
          </span>
        </li>
      </ul>

      <div class="mt-6 rounded-xl border border-slate-800 bg-slate-950 p-4">
        <p class="text-sm text-slate-400">Estimated brute-force crack time</p>

        <p class="mt-2 text-2xl font-bold text-cyan-400">
          {{ crackTimeLabel }}
        </p>

        <p class="mt-2 text-sm text-slate-400">
          Estimate assumes 1 billion guesses per second and no password leaks,
          reuse, phishing or personal information clues.
        </p>
      </div>

      <div class="mt-6">
        <TipCard
          :description="[
            'Avoid using names, birthdays, pets, favourite teams or anything someone could guess from your social media.',
          ]"
          :is-dark="true"
        />
      </div>
    </section>
  </main>
</template>
