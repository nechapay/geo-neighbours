<script setup>
import { ref } from 'vue'
</script>
<template>
  <div class="dialog-wrapper fill base-flex flex-column">
    <div class="dialog-body base-flex flex-column"></div>
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
</style>
