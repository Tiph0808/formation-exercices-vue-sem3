<script setup>
import { wordsList } from '@/utils/data'

// definition evenement :
const emit = defineEmits(['correctTheWord'])
</script>

<template>
  <button v-for="word in wordsList" :key="word" @click="$emit('correctTheWord', word)">
    {{ word }}
  </button>
</template>

<style scoped>
button {
  background-color: aquamarine;
}
</style>
