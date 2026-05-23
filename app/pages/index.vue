<template>
  <main class="mx-auto max-w-6xl px-6 py-10 text-white">
    <section class="mb-10">
      <p class="mb-2 text-2xl font-medium text-cyan-400">
        Dashboard
      </p>
      <p class="max-w-2xl text-slate-300">
        Improve your digital safety habits by practising basic cybersecurity skills through simple
        tools, checklists and awareness tips.
      </p>
    </section>

    <section class="mb-10 grid gap-6 md:grid-cols-3">
      <div class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
        <p class="text-sm text-slate-400">Risk Score</p>
        <p class="mt-2 text-5xl font-bold text-yellow-400">72</p>
        <p class="mt-2 text-sm text-slate-300">Moderate risk</p>
      </div>

      <div class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
        <p class="text-sm text-slate-400">Completed Tools</p>
        <p class="mt-2 text-5xl font-bold text-cyan-400">1/4</p>
        <p class="mt-2 text-sm text-slate-300">Start with the password checker.</p>
      </div>

      <div class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
        <p class="text-sm text-slate-400">Security Level</p>
        <p class="mt-2 text-5xl font-bold text-emerald-400">Basic</p>
        <p class="mt-2 text-sm text-slate-300">Build better habits step by step.</p>
      </div>
    </section>

    <section>
      <h2 class="mb-4 text-2xl font-semibold">
        Security Tips
      </h2>

      <div class="grid gap-4 md:grid-cols-2">
        <div
          v-for="tip in tips"
          :key="tip.title"
          class="rounded-2xl border border-slate-800 bg-slate-900 p-5"
        >
          <p class="mb-2 text-lg font-semibold">
            {{ tip.title }}
          </p>
          <p class="text-sm text-slate-300">
            {{ tip.description }}
          </p>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
const tips = [
  {
    title: 'Use unique passwords',
    description: 'Avoid reusing the same password across multiple accounts.',
  },
  {
    title: 'Enable multi-factor authentication',
    description: 'Use an authenticator app where possible.',
  },
  {
    title: 'Check links before clicking',
    description: 'Look for misspellings, strange domains and urgent language.',
  },
  {
    title: 'Keep software updated',
    description: 'Even the smallest updates can often fix security vulnerabilities.',
  },
]
</script>