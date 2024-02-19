<script setup lang="ts">

const props = defineProps({ roles: { type: Array, required: true } })

props.roles

const emit = defineEmits(['change'])

function setRole(role: string) {
  emit('change', role)
}
</script>

<template>
  <div class="list-group">
    <a class="list-group-item"
       href="#details"
       v-for="role in roles"
       :key="role"
       @click="setRole(role)"
       data-bs-toggle="modal"
    >
      {{ role }}
    </a>
  </div>
</template>
