<script setup lang="ts">
const selectedModule = ref('')

defineProps<{
  modules: {
    title: string
    path: string
  }[]
}>()

function goToModule() {
  if (selectedModule.value) {
    navigateTo(selectedModule.value)
  }
}
</script>

<template>
  <select
    v-model="selectedModule"
    @change="goToModule"
    class="rounded-lg border border-slate-700 bg-slate-900 px-3 py-2 text-white"
  >
    <option value="">
      Jump to module…
    </option>

    <option
      v-for="module in modules"
      :key="module.path"
      :value="module.path"
    >
      {{ module.title }}
    </option>
  </select>
</template>