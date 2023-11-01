<script setup>
const props = defineProps(['teams'])
const emits = defineEmits(['close'])

function handleClose() {
  emits('close')
}
</script>
<template>
  <div class="dialog-wrapper fill base-flex flex-column" @click.self="handleClose">
    <div class="dialog-body base-flex flex-column">
      <h2 class="dialog-title base-flex">Настройки</h2>
      <div class="dialog-text base-flex flex-column">
        <div class="input-group base-flex flex-column" v-for="(item, index) in teams" :key="item.id">
          <label :for="`input_${item.id}`">Команда {{ index + 1 }}</label>
          <input :id="`input_${item.id}`" class="team-input" v-model="item.name" />
        </div>
      </div>
      <div class="dialog-controls base-flex flex-column">
        <button class="my-button" @click="handleClose">Закрыть</button>
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
  height: 50%;
  width: 30%;
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
  height: 80%;
  border-bottom: 1px solid #fb9d23;
  font-size: 100%;
  width: 100%;
  overflow-y: auto;
}
.dialog-controls {
  height: 10%;
  justify-content: space-between;
  min-width: 100%;
}
.input-group {
  align-items: flex-start;
}
.team-input {
  font-size: 150%;
}
</style>
