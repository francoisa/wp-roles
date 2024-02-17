<script setup lang="ts">
  const props = defineProps({
    roles: { type: Array, required: true },
  })

  props.roles
</script>

<template>
  <ul>
    <li v-for="role in roles" :key="role">{{ role }}</li>
  </ul>
</template>
