<script setup>
const emit = defineEmits(['getRandomColor'])
</script>

<template>
  <button @click="$emit('getRandomColor')">Couleur surprise</button>
</template>

<style scoped></style>
