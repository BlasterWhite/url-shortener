<script setup lang="ts">
  import { RouterView } from 'vue-router'
  import BaseNavBar from '@/components/BaseNavBar.vue'
</script>

<template>
  <header>
    <base-nav-bar />
  </header>

  <RouterView />
</template>

<style scoped></style>
