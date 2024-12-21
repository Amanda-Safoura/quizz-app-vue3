<template>
  <div>
    <div class="mb-3">
      <div class="form-check form-check-inline">
        <input
          class="form-check-input"
          type="radio"
          :id="`radio-${id}`"
          :name="name"
          :value="value"
          @change="onCheck"
        />
        <label class="form-check-label" :for="`radio-${id}`">{{ radioLabel }}</label>
      </div>
    </div>
  </div>
</template>

<script setup>
const emits = defineEmits(['check'])

const onCheck = (event) => {
  if (event.currentTarget.checked) emits('check', event.currentTarget.value)
}

defineProps({
  id: String,
  name: String,
  value: String,
  radioLabel: String
})
</script>
