<script setup lang="ts">
defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="text-center">
    <h1 class="display-5 fw-bold">{{ msg }}</h1>
    <h3></h3>
  </div>
</template>

