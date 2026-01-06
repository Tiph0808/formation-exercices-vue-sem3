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

    <div class="not-connected" v-else>
      <button @click="connectUser">S'inscrire</button>
      <button @click="connectUser">Se connecter</button>
    </div>
  </div>
</template>
<style scoped>
div {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  margin-bottom: 30px;
}

div > button {
  padding: 5px 8px;
  border: none;
  color: white;
  background-color: green;
  border-radius: 20px;
}

.not-connected button {
  padding: 5px 8px;
  border: 2px solid green;
  color: green;
  background-color: white;
  border-radius: 20px;
}
</style>
