<script setup>
import { RouterView } from 'vue-router'
import Header from './HeaderPage.vue'
</script>

<template>
  <div class="container-fluid">
    <Header />
    <RouterView />
  </div>
</template>

<style scoped></style>
