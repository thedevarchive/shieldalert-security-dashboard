<template>
  <aside class="sticky top-24 hidden h-fit w-64 rounded-2xl border border-slate-800 bg-slate-900 p-4 lg:block">
    <p class="mb-3 text-sm font-semibold text-slate-400">
      On this page
    </p>

    <nav class="space-y-2 text-sm">
      <a
        v-for="section in sections"
        :key="section.id"
        :href="`#${section.id}`"
        class="block rounded-lg px-3 py-2 text-slate-300 hover:bg-slate-800 hover:text-white"
      >
        {{ section.title }}
      </a>
    </nav>
  </aside>
</template>

<script setup lang="ts">
defineProps<{
  sections: {
    id: string
    title: string
  }[]
}>()
</script>