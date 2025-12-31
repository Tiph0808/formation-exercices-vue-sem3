<script setup>
import { ref } from 'vue'
const wallet = ref(0)

const addOneEuro = () => {
  wallet.value++
}
const addFiveEuros = () => {
  wallet.value = wallet.value + 5
}
</script>
<template>
  <div>
    <p v-if="wallet === 0">😱Mon porte-monnaie est vide</p>
    <p v-else-if="wallet === 1">Mon premier euro ! 🤩</p>
    <p v-else-if="wallet > 30">🍾 &Ccedil;a y est je suis riche !! 🍾</p>
    <p v-else-if="wallet > 10">Yes ! Plus de 10 euros !</p>

    <p>{{ wallet }} €</p>
  </div>
  <div>
    <button @click="addOneEuro">Ajouter 1€</button>
    <!-- on aurait pu simplifier en mettant la logique à executer entre les guillements du else if : v-else-if="wallet++" -->
    <button @click="addFiveEuros">Ajouter 5€</button>
    <!-- pareil ici : v-else-if="wallet +=5" -->
  </div>
</template>
<style scoped></style>
