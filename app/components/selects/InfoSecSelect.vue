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
  {
    title: 'Security Management Frameworks and Controls Management',
    path: '/courses/infosec-mgmt/module3',
  },
]
</script>

<template>
  <ModuleSelect :modules="modules" />
</template>