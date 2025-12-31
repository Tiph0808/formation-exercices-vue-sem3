<script setup>
import { ref } from 'vue'
const isConnected = ref(false)
const connectUser = () => {
  isConnected.value = true
}
</script>
<template>
  <div>
    <button v-if="isConnected" @click="isConnected = false">Se déconnecter</button>

    <div v-else>
      <button @click="connectUser">S'inscrire</button>
      <button @click="connectUser">Se connecter</button>
    </div>
  </div>
</template>
<style scoped></style>
