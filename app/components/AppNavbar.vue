<script setup>
import { ShieldCog } from '@lucide/vue';
</script>

<template>
  <nav class="relative z-50 border-b border-slate-800 bg-slate-950 text-white">
    <div class="flex max-w-6xl items-center justify-between px-6 py-4">
      <NuxtLink to="/" class="text-xl font-bold">
        <div class="flex items-center text-cyan-400">
          <ShieldCog class="h-10 w-10 mx-1" />
          <h1 class="text-3xl font-bold my-1">
            ShieldAlert
          </h1>
        </div>
      </NuxtLink>

      <div class="flex gap-20 px-20">
        <div class="relative group">
          <button class="text-xl font-semibold text-slate-300 hover:text-white">
            Tools
          </button>

          <div class="absolute left-1/2 -translate-x-1/2 top-full hidden pt-2 group-hover:block">
            <div class="min-w-56 rounded-lg border border-slate-800 bg-slate-900 p-2 shadow-lg">
              <NuxtLink to="/password-checker" class="block rounded px-3 py-2 hover:bg-slate-800">
                Password Checker
              </NuxtLink>

              <NuxtLink to="/phishing-quiz" class="block rounded px-3 py-2 hover:bg-slate-800">
                Phishing Quiz
              </NuxtLink>

              <NuxtLink to="/suspicious-link" class="block rounded px-3 py-2 hover:bg-slate-800">
                Link Checklist
              </NuxtLink>

              <NuxtLink to="/breach-response" class="block rounded px-3 py-2 hover:bg-slate-800">
                Breach Response
              </NuxtLink>
            </div>
          </div>
        </div>

        <div class="relative group">
          <button class="text-xl font-semibold text-slate-300 hover:text-white">
            Courses
          </button>

          <div class="absolute left-1/2 -translate-x-1/2 top-full hidden pt-2 group-hover:block">
            <div class="min-w-56 rounded-lg border border-slate-800 bg-slate-900 p-2 shadow-lg">
              <NuxtLink to="/courses/infosec-mgmt/course1" class="block rounded px-3 py-2 hover:bg-slate-800">
                Information Security Management
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>