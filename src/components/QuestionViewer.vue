<script setup>
import { ref, computed } from 'vue'
import SwInput from './SwInput.vue'

const emits = defineEmits(['close', 'updateScore'])
const props = defineProps(['question', 'teams'])
function handleCloseClick() {
  emits('close')
}

let localIndex = ref(0)

const inputs = ref([false, false, false, false])
const checked = ref(true)
const inputVisible = ref([true, true, true, true])
const finished = ref(false)

const displayedText = computed(() => {
  if (localIndex.value < props.question.questions.length && inputVisible.value.indexOf(true) !== -1)
    return props.question.questions[localIndex.value].text
  finished.value = true
  return props.question.answer
})

function handleNext() {
  for (let i = 0; i < inputs.value.length; i++) {
    if (inputs.value[i] && inputVisible.value[i]) emits('updateScore', i, localIndex.value)
    inputVisible.value[i] = !inputs.value[i]
  }
  if (localIndex.value < props.question.questions.length - 1) localIndex.value++
  else {
    for (let i = 0; i < inputVisible.value.length; i++) {
      inputVisible.value[i] = false
      finished.value = true
    }
  }
}
</script>

<template>
  <div class="dialog-wrapper fill base-flex flex-column">
    <div class="dialog-body base-flex flex-column">
      <h2 class="dialog-title base-flex">{{ question.title }}</h2>
      <div class="dialog-text base-flex">
        <span :class="{ finish: finished }">{{ displayedText }}</span>
      </div>

      <div class="dialog-controls base-flex flex-column">
        <div class="switch-container base-flex">
          <SwInput
            v-model="inputs[index]"
            :value="inputs[index]"
            :label="item.name"
            v-for="(item, index) in teams"
            :key="item.id"
            v-show="inputVisible[index]"
          />
        </div>
        <Transition name="fade" mode="out-in">
          <button v-if="!finished" class="my-button" @click="handleNext">Далее</button>
          <button v-else-if="finished" class="my-button close-button" @click="handleCloseClick">Закрыть</button>
        </Transition>
      </div>
    </div>
  </div>
</template>

<style scoped>
.dialog-wrapper {
  z-index: 2;
  position: fixed;
  top: 0;
  left: 0;
}

.dialog-body {
  background: white;
  height: 70%;
  width: 60%;
  border: 1px solid #fb9d23;
  padding: 2%;
  font-size: 100%;
  text-align: justify;
  box-shadow: 5px 5px 5px rgba(19, 18, 18, 0.432);
}
.dialog-title {
  height: 10%;
  width: 100%;
  border-bottom: 1px solid #fb9d23;
  align-items: flex-start;
  font-weight: bolder;
}

.dialog-text {
  height: 60%;
  border-bottom: 1px solid #fb9d23;
  font-size: 150%;
  width: 100%;
  overflow-y: auto;
}

.dialog-controls {
  height: 30%;
  justify-content: space-between;
  min-width: 100%;
}

.finish {
  font-size: 300%;
}
</style>
