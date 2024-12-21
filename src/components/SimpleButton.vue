<template>
  <button :type="type || 'button'" class="btn" :disabled="disabled"><slot></slot></button>
</template>

<script setup>
defineProps({
  type: String,
  disabled: Boolean
})
</script>
