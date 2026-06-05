<template>
  <main class="mx-auto max-w-4xl px-6 py-10 text-white">
    <section class="mb-8">
      <h1 class="mb-3 text-4xl font-bold">
        Breach Response Checklist
      </h1>

      <p class="text-slate-300">
        Follow these steps if you think one of your accounts has been compromised.
      </p>
    </section>

    <!-- checklist user should tick when they accomplish the steps for their account -->
    <section class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
      <div v-for="item in checklist" :key="item.title" class="mb-4 rounded-xl border border-slate-800 bg-slate-950 p-5">
        <div class="flex items-start gap-4">
          <input v-model="item.completed" type="checkbox" class="mt-5 h-5 w-5 accent-cyan-400" />
          <div>
            <p class="mb-2 text-lg font-semibold">
              {{ item.title }}
            </p>

            <p class="text-sm text-slate-300">
              {{ item.description }}
            </p>
          </div>
        </div>
      </div>

      <div class="mt-6">
        <div class="mb-2 flex items-center justify-between">
          <span class="text-sm text-slate-300">
            Progress
          </span>

          <span class="text-sm font-semibold text-cyan-400">
            {{ completedSteps }}/{{ checklist.length }}
          </span>
        </div>

        <div class="h-3 rounded-full bg-slate-800">
          <div class="h-3 rounded-full bg-cyan-400 transition-all" :style="{ width: `${progress}%` }" />
        </div>
      </div>

      <div class="mt-6">
        <TipCard :title="'Important'"
          :description="['If your banking details, identity documents or workplace credentials were exposed, contact the relevant organisation immediately.']"
          :icon="TriangleAlert" />
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
import { TriangleAlert } from '@lucide/vue'

type ChecklistItem = {
  title: string
  description: string
  completed: boolean
}

const checklist = ref<ChecklistItem[]>([
  {
    title: 'Change your password',
    description:
      'Create a new strong password that is unique to this account.',
    completed: false,
  },
  {
    title: 'Enable multi-factor authentication',
    description:
      'Add an extra layer of protection using an authenticator app if possible.',
    completed: false,
  },
  {
    title: 'Check for suspicious activity',
    description:
      'Review login history, sent emails, transactions, and connected devices.',
    completed: false,
  },
  {
    title: 'Log out other devices',
    description:
      'Sign out all active sessions to remove unauthorised access.',
    completed: false,
  },
  {
    title: 'Warn contacts if needed',
    description:
      'Tell friends, coworkers, or clients if your account may have sent phishing messages.',
    completed: false,
  },
  {
    title: 'Scan your device',
    description:
      'Run antivirus or security scans if malware may have been involved.',
    completed: false,
  },
])

//get number of steps ticked
const completedSteps = computed(() => {
  return checklist.value.filter((item) => item.completed).length
})

//calculate progress bar value for UI 
const progress = computed(() => {
  return (completedSteps.value / checklist.value.length) * 100
})
</script>