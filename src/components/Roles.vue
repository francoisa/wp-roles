<script setup lang="ts">
  const props = defineProps({
    roles: { type: Array, required: true },
  })

  props.roles
</script>

<template>
  <ul class="list-group">
    <li class="list-group-item" v-for="role in roles" :key="role">{{ role }}</li>
  </ul>
</template>
