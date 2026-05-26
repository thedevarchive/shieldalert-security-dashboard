<script setup lang="ts">
defineProps<{
    title: string
    description: string[]
    icon: any
}>()
</script>

<template>
    <div class="rounded-2xl border border-slate-800 bg-slate-900 p-6">
        <div class="flex">
            <component :is="icon" class="mb-4 mr-2 text-cyan-400" :size="25" />

            <p class="mb-2 text-lg font-semibold text-cyan-400">
                {{ title }}
            </p>
        </div>

        <p class="text-sm text-slate-300" v-for="(item, index) in description" :key="index">
            {{ item }}
        </p>
    </div>
</template>