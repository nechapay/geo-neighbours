<script setup>
import Copyright from './components/Copyright.vue'
import StartPage from './components/StartPage.vue'
import EndPage from './components/EndPage.vue'
import MainPage from './components/MainPage.vue'
import { ref } from 'vue'

let started = ref(false)
let ended = ref(false)

function handleStarted() {
  started.value = true
}

const winners = ref([])

function handleEnded(val) {
  winners.value = val
  ended.value = true
}
</script>

<template>
  <Transition name="fade" mode="out-in">
    <start-page v-if="!started && !ended" @started="handleStarted" />
    <main-page v-else-if="started && !ended" @ended="handleEnded" />
    <end-page v-else-if="ended" :winners="winners" />
  </Transition>
  <Copyright />
</template>

<style scoped></style>
