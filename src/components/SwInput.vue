<script setup>
import { computed } from 'vue'
const props = defineProps({
  modelValue: { type: [Array, Boolean] },
  value: { type: [Boolean, Object] },
  label: { type: String }
})
const emit = defineEmits(['update:modelValue'])
const model = computed({
  get() {
    return props.modelValue
  },
  set(value) {
    emit('update:modelValue', value)
  }
})
</script>
<template>
  <div class="switch-container base-flex flex-column">
    <span class="switch-label">{{ label }}</span>
    <label class="switch">
      <input type="checkbox" v-model="model" :value="value" />
      <span class="slider round"></span>
    </label>
  </div>
</template>

<style scoped>
.switch-container {
  margin-right: 2vh;
}

.switch {
  position: relative;
  display: inline-block;
  width: 6vh;
  height: 3.4vh;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #faa;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: '';
  height: 2.6vh;
  width: 2.6vh;
  left: 0.4vh;
  bottom: 0.4vh;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #afa;
}

input:focus + .slider {
  box-shadow: 0 0 1px #afa;
}

input:checked + .slider:before {
  -webkit-transform: translateX(2.6vh);
  -ms-transform: translateX(2.6vh);
  transform: translateX(2.6vh);
}

.slider.round {
  border-radius: 3.4vh;
}

.slider.round:before {
  border-radius: 50%;
}

.switch-label {
  font-size: 100%;
}
</style>
