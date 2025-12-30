<script setup>
import { ref, reactive, computed } from 'vue'

const numbers = ref([76, 876, 467, 2, 67, 3, 90, 7, 678])

const average = computed(() => {
  let total = 0
  for (let i = 0; i < numbers.value.length; i++) {
    total = total + numbers.value[i]
  }
  return total / numbers.value.length
})

const addNumber = () => {
  const randomNumber = Math.floor(Math.random() * 1000)
  numbers.value.push(randomNumber)
}
</script>

<template>
  <p>{{ numbers }}</p>
  <p>{{ average }}</p>
  <button @click="addNumber">Ajouter un nombre aléatoire</button>
</template>
<style scoped></style>
