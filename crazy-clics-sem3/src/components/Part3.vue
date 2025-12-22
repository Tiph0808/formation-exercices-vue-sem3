<script setup>
// import des donnees necessaires du fichier data.js
import { numbersList } from '../utils/data.js'
// console.log(numbersList)

const emit = defineEmits(['convertToCm'])
</script>

<template>
  <button v-for="number in numbersList" :key="number" @click="$emit('convertToCm', number)">
    {{ number }}
  </button>
</template>

<style></style>
