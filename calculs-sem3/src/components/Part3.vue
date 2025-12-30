<script setup>
import { ref, computed } from 'vue'

const user = {
  firstName: 'Toto',
  lastName: 'Smith',
}

const currentTime = ref(new Date().getHours())
console.log(currentTime.value)

const welcomingLine = computed(() => {
  if (currentTime.value > 0 && currentTime.value < 12) {
    return `Bonjour`
  } else if (currentTime.value >= 12 && currentTime.value < 18) {
    return `Bon après-midi`
  } else {
    return `Bonsoir`
  }
})

const morningTime = () => {
  currentTime.value = 8
}

const afternoonTime = () => {
  currentTime.value = 15
}
const eveningTime = () => {
  currentTime.value = 22
}
</script>
<template>
  <p>{{ welcomingLine }}, {{ user.firstName }} {{ user.lastName }} !</p>

  <button @click="morningTime">Heure de la matinée</button>
  <button @click="afternoonTime">Heure de l'après-midi</button>
  <button @click="eveningTime">Heure de la soirée</button>
</template>
<style scoped></style>
