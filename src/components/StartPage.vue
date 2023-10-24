<script setup>
const emits = defineEmits(['started'])
function handleStartClick() {
  emits('started')
}
</script>
<template>
  <div class="title-screen fill">
    <div class="title">Геополитическое положение России</div>
    <a @click="handleStartClick" class="my-button start-page__button">Начать</a>
  </div>
</template>

<style scoped>
.title-screen {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.title {
  font-family: DINpro, serif;
  font-size: 300%;
  color: #d51212;
  margin: 4%;
}

.title-screen p {
  width: auto;
  text-align: center;
  font-size: 150%;
  background-color: white;
  text-justify: distribute;
  box-shadow: 5px 5px 5px #242222c2;
  border-radius: 1rem;
  padding: 2%;
}
.start-page__button {
  font-family: DINpro, serif;
  margin-top: 4%;
  font-size: 300%;
  padding: 8px 24px;
}
</style>
