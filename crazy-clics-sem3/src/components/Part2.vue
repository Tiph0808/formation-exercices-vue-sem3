<script setup>
const emit = defineEmits(['getRandomColor'])
</script>

<template>
  <button @click="$emit('getRandomColor')">Couleur surprise</button>
</template>

<style scoped>
button {
  font-size: 18px;
  font-weight: bold;
  background-color: white;
  color: lightskyblue;
  border: 3px solid lightskyblue;
  border-radius: 30px;
}
</style>
