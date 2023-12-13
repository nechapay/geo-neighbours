<script setup>
import { ref } from 'vue'
const props = defineProps(['state'])
const emits = defineEmits(['close'])
function handleCloseClick() {
  emits('close')
}
</script>
<template>
  <div class="dialog-wrapper fill">
    <div class="dialog-body base-flex flex-column">
      <div class="state-name">{{ state.name }}</div>
      <div class="flag" :class="state.flag"></div>
      <div class="capital"><b>Столица:</b>{{ state.capital }}</div>
      <div class="description">{{ state.desc }}</div>
    </div>
    <div class="dialog-controls base-flex flex-column">
      <button class="my-button close-button" @click="handleCloseClick">Закрыть</button>
    </div>
  </div>
</template>

<style scoped>
.dialog-wrapper {
  z-index: 2;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
}

.dialog-body {
  background: white;
  height: 80%;
  width: 20%;
  border: 1px solid #fb9d23;
  padding: 2%;
  font-size: 100%;
  text-align: justify;
  box-shadow: 5px 5px 5px rgba(19, 18, 18, 0.432);
  justify-content: flex-start;
  margin-right: 0.5%;
}

.dialog-body * {
  margin: 5px 0;
}

.dialog-controls {
  width: 20%;
  position: relative;
  top: -7%;
}
</style>
