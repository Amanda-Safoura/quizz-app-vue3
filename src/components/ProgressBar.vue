<template>
  <div
    class="progress"
    role="progressbar"
    :aria-label="label"
    :aria-valuenow="progressValue"
    aria-valuemin="0"
    aria-valuemax="100"
    :style="{ height: height || '20px' }"
  >
    <div class="progress-bar" role="progressbar" :style="{ width: `${progressValue}%` }">
      {{ progressValue > 5 ? progressValue + '%' : '' }}
    </div>
  </div>
</template>
<script setup>
defineProps({
  progressValue: Number,
  label: String,
  height: String
})
</script>
