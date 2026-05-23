<script setup>
import { ShieldCog } from '@lucide/vue';
</script>

<template>
  <nav class="border-b border-slate-800 bg-slate-950 text-white">
    <div class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
      <NuxtLink to="/" class="text-xl font-bold">
        <div class="flex justify-center text-cyan-400">
          <ShieldCog class="h-10 w-10 mx-1"/>
          <h1 class="text-3xl font-bold my-1">
            ShieldAlert
          </h1>
        </div>
      </NuxtLink>

      <div class="flex gap-4 text-sm text-slate-300">
        <NuxtLink to="/password-checker" class="hover:text-white">Password Checker</NuxtLink>
        <NuxtLink to="/phishing-quiz" class="hover:text-white">Phishing Quiz</NuxtLink>
        <NuxtLink to="/suspicious-link" class="hover:text-white">Link Checklist</NuxtLink>
        <NuxtLink to="/breach-response" class="hover:text-white">Breach Response</NuxtLink>
      </div>
    </div>
  </nav>
</template>