<script setup lang="ts">
const modules = [
  {
    title: 'Information Security Fundamentals',
    path: '/courses/infosec-mgmt/module1',
  },
  {
    title: 'Risk Statements',
    path: '/courses/infosec-mgmt/module2',
  },
]
</script>

<template>
  <ModuleSelect :modules="modules" />
</template>