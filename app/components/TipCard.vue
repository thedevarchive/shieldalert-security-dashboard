<script setup lang="ts">
import { Lightbulb } from '@lucide/vue';

withDefaults(
defineProps<{
    title?: string
    description: string[]
    icon?: any
    isDark?: boolean 
}>(), 
    {
        title: "Tip", 
        icon: () => Lightbulb, 
        isDark: false
    }
)
</script>

<template>
    <div class="rounded-2xl border border-slate-800 p-6 mt-6"
        :class="isDark ? 'bg-slate-950' : 'bg-slate-900'">
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