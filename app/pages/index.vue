<script setup lang="ts">
import TipCard from '~/components/TipCard.vue'
import { CreditCard, Fish, FishingHook, Info, Lightbulb, Link2, LockKeyholeOpen, MailQuestionMark, MailWarning, PhoneMissed, RectangleEllipsis, RotateCcwKey, ScreenShareOff, Shredder, UserLock, VenetianMask } from '@lucide/vue';

useHead({
  title: 'Home',
})

// list of general tips 
const generalTips = [
  {
    title: 'Use unique passwords',
    description: 'Avoid reusing the same password across multiple accounts.',
  },
  {
    title: 'Enable multi-factor authentication',
    description: 'Use an authenticator app if possible.',
  },
  {
    title: 'Check links before clicking',
    description: 'Look for misspellings, strange domains and urgent language.',
  },
  {
    title: 'Keep software updated',
    description: 'Even the smallest patches can often fix security vulnerabilities.',
  },
]

//randomly show one of these tips 
const randomTips = [
  {
    title: 'Never share your OTP or password',
    description: 'Legitimate support staff should not ask for your OTP, verification code or password.',
    icon: UserLock
  },
  {
    title: 'Be careful with remote access apps',
    description: 'Scammers may ask you to install remote access software so they can control your device.',
    icon: ScreenShareOff
  },
  {
    title: 'Check email urgency',
    description: 'Phishing messages often pressure you to act quickly without thinking.',
    icon: MailWarning
  },
  {
    title: 'Use unique passwords',
    description: 'Reusing passwords could put your other accounts at risk.',
    icon: RectangleEllipsis
  },
  {
    title: 'Verify links before clicking',
    description: 'Hover over links and check the domain carefully before entering personal details.',
    icon: Link2
  },
  {
    title: '\"Forgot password?\" is an option',
    description: 'It\'s better to forget passwords than to reuse a password you remember.',
    icon: RotateCcwKey
  },
  {
    title: 'Verify workplace messages',
    description: 'Scammers may impersonate managers, founders, bosses or IT staff. Verify unexpected requests from workplace authorities, especially if they ask for sensitive information.',
    icon: MailQuestionMark
  },
  {
    title: 'Do not accept calls from \"Scam Likely\"',
    description: 'If a contact\'s name says \"Scam Likely\", that means that your phone is warning you not to answering it.',
    icon: PhoneMissed
  },
  {
    title: 'Do not use personal details in your password',
    description: 'Avoid passwords based on names, birthdays, favourite teams or simple number patterns.',
    icon: VenetianMask
  },
  {
    title: 'Avoid creating a password that is easy to guess',
    description: 'Do not use one word as a password. A good password must have at least one uppercase letter, one lowercase letter, a number and a symbol (e.g. !, @, *, _).',
    icon: LockKeyholeOpen
  },
  {
    title: 'What is phishing?',
    description: 'Phishing is a cybercrime where attackers pretend to be a legitimate organisation through their emails in the hopes of unsuspecting victims disclosing their credentials to the attacker.',
    icon: Fish
  },
  {
    title: 'Know the difference',
    description: 'Vishing, or voice phishing, is phishing but done through calls. Spear phishing targets individuals in a certain organisation. Whaling targets high-ranking or more popular individuals.',
    icon: FishingHook
  },
  {
    title: 'DO NOT REDEEM',
    description: 'Gift card scams often pressure victims into acting quickly.',
    icon: CreditCard
  },
  {
    title: 'Delete there files',
    description: '*their',
    icon: Shredder
  },
]

const randomTip = ref<(typeof randomTips)[number] | null>(null)

// onMounted function ensures that icon is rendered properly
onMounted(() => {
  const index = Math.floor(Math.random() * randomTips.length)

  const selectedTip = randomTips[index]

  if (!selectedTip) return

  randomTip.value = selectedTip
})
</script>

<template>
  <main class="mx-auto max-w-6xl px-6 py-10 text-white">
    <section class="mb-10">
      <p class="mb-2 text-2xl font-bold text-cyan-400">
        Welcome
      </p>
      <p class="text-sm text-slate-300">
        Improve your digital safety habits by practising basic cybersecurity skills through simple
        tools, checklists and awareness tips.
      </p>
    </section>

    <section>
      <div class="flex">
        <Info class="h-6 w-6 mx-2 mt-1" />
        <h2 class="mb-4 text-2xl font-semibold">
          Security Tips
        </h2>
      </div>

      <div class="mb-10 grid gap-4 md:grid-cols-2">
        <div v-for="tip in generalTips" :key="tip.title" class="rounded-2xl border border-slate-800 bg-slate-900 p-5">
          <p class="mb-2 text-lg font-semibold">
            {{ tip.title }}
          </p>
          <p class="text-sm text-slate-300">
            {{ tip.description }}
          </p>
        </div>
      </div>
    </section>

    <section>
      <div class="flex">
        <Lightbulb class="h-6 w-6 mx-2 mt-1" />
        <h2 class="mb-4 text-2xl font-semibold">
          User Advisory
        </h2>
      </div>

      <div v-if="randomTip">
        <TipCard :title="randomTip.title" :description="[randomTip.description]" :icon="randomTip.icon" />
      </div>
    </section>
  </main>
</template>
