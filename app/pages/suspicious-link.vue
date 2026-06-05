<template>
  <main class="mx-auto max-w-4xl px-6 py-10 text-white">
    <section class="mb-8">
      <h1 class="mb-3 text-4xl font-bold">
        Suspicious Link Checklist
      </h1>

      <p class="text-slate-300">
        Analyse a URL for common phishing and scam indicators.
      </p>
    </section>

    <section class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
      <label for="link" class="mb-2 block text-sm font-medium text-slate-300">
        Paste a link
      </label>

      <input id="link" v-model="link" type="text" placeholder="https://example.com"
        class="w-full rounded-xl border border-slate-700 bg-slate-950 px-4 py-3 text-white outline-none focus:border-cyan-400" />

      <div class="mt-6">
        <div class="mb-2 flex items-center justify-between">
          <span class="text-sm text-slate-300">Risk Level</span>

          <span class="text-sm font-semibold" :class="riskTextClass">
            {{ riskLabel }}
          </span>
        </div>

        <div class="h-3 rounded-full bg-slate-800">
          <div class="h-3 rounded-full transition-all" :class="riskBarClass" :style="{ width: `${riskScore}%` }" />
        </div>
      </div>

      <ul class="mt-6 space-y-3">
        <li v-for="check in checks" :key="check.label" class="flex items-center gap-3 text-sm">
          <span class="flex h-5 w-5 items-center justify-center rounded-full text-xs" :class="!link ? 'bg-gray-500' : (check.failed
            ? 'bg-red-500 text-white'
            : 'bg-emerald-500 text-white')">
            {{ !link ? '-' : ( check.failed ? '!' : '✓' ) }}
          </span>

          <span :class="check.failed
            ? 'text-red-300'
            : 'text-slate-300'">
            {{ check.label }}
          </span>
        </li>
      </ul>
        
      <div class="mt-6">
        <TipCard
          :title="'Reminders'"
          :description="[
            '• A link can still be malicious even if it looks normal.',
            '• A link can also be normal even if it is suspicious.', 
            '• Always verify unexpected login pages, invoices, downloads or urgent requests.',
            '• As this is only a simple link checker, you may need to verify the context and sender to ensure the link is not suspicious.'
            ]"
          :is-dark="true" />
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
const link = ref('') //state for user-inputted suspicious link 

//similar to password checker, the link is tested against boolean conditions or regexes in the failed properties 
const checks = computed(() => {
  const value = link.value.toLowerCase() //set link to lowercase 

  return [
    {
      label: 'Uses HTTPS',
      failed: value.length > 0 && !value.startsWith('https://'),
    },
    {
      label: 'Contains suspicious words',
      failed: /(login|verify|secure|update|banking|confirm)/.test(value),
    },
    {
      label: 'Contains many numbers or symbols',
      failed: /[\d]{4,}|@|%/.test(value),
    },
    {
      label: 'Uses a suspicious domain ending',
      failed: /\.(ru|tk|xyz|click|top)/.test(value),
    },
    {
      label: 'Contains misspelled brand names',
      failed: /(paypa|micr0soft|amaz0n|goog1e)/.test(value),
    },
    {
      label: 'Very long or messy URL',
      failed: value.length > 80,
    },
  ]
})

//get number of failed checks (aka how many red flags the link fulfils)
const failedChecks = computed(() => {
  return checks.value.filter((check) => check.failed).length
})

//calculate risk score
//(each red flag increases the risk score by 20)
const riskScore = computed(() => {
  if (!link.value) return 0

  return Math.min(failedChecks.value * 20, 100)
})

//show risk status to user 
const riskLabel = computed(() => {
  if (!link.value) return 'Not tested'
  if (riskScore.value < 25) return 'Little to no red flags'
  if (riskScore.value < 50) return 'Some red flags'
  if (riskScore.value < 75) return 'Many red flags detected'
  return 'Very suspicious'
})

const riskBarClass = computed(() => {
  if (riskScore.value < 25) return 'bg-emerald-400'
  if (riskScore.value < 50) return 'bg-yellow-400'
  if (riskScore.value < 75) return 'bg-orange-400'
  return 'bg-red-500'
})

const riskTextClass = computed(() => {
  if (riskScore.value < 25) return 'text-emerald-400'
  if (riskScore.value < 50) return 'text-yellow-400'
  if (riskScore.value < 75) return 'text-orange-400'
  return 'text-red-400'
})
</script>