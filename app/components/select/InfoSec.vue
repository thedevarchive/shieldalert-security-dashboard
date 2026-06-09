<script setup lang="ts">
const modules = [
  {
    title: 'Information Security Fundamentals',
    path: '/courses/infosec-mgmt/module1',
  },
  {
    title: 'Security Incidents and Attacks',
    path: '/courses/infosec-mgmt/module2',
  },
  {
    title: 'Risk Statements',
    path: '/courses/infosec-mgmt/module3',
  },
  {
    title: 'Security Management Frameworks',
    path: '/courses/infosec-mgmt/module4',
  },
]
</script>

<template>
  <CoursesSelect :modules="modules" />
</template>