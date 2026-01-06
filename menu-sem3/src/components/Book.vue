<script setup>
const props = defineProps({
  selection: Object,
  average: Number,
})

import { ref } from 'vue'

const shortStyle = ref(true)

const changeStyle = () => {
  shortStyle.value = !shortStyle.value
}
</script>

<template>
  <section class="content-card">
    <h2>{{ selection.title }}</h2>

    <div v-if="shortStyle" class="text">
      <p v-for="paragraph in selection.synopsis.split('\n')">{{ paragraph }}</p>
      <button @click="changeStyle"><font-awesome-icon :icon="['fas', 'caret-down']" /></button>
    </div>

    <div v-else class="otherText">
      <p v-for="paragraph in selection.synopsis.split('\n')">{{ paragraph }}</p>
      <button @click="changeStyle"><font-awesome-icon :icon="['fas', 'caret-up']" /></button>
    </div>

    <div class="author">
      <p v-if="selection.author">{{ selection.author }}</p>
    </div>
    <div class="rates" v-if="selection.rates.length > 0">
      <font-awesome-icon :icon="['fas', 'thumbs-up']" />
      <span>{{ average }}</span>
    </div>
    <p class="rates" v-else>Pas encore de like</p>
    <div class="small-book" v-if="selection.numberOfPage < 250">
      <p>Petit</p>
      <p>Livre</p>
    </div>
  </section>
</template>

<style scoped>
@import '../assets/style.css';

.text {
  /* border: 1px solid gray; */
  display: flex;
  flex-direction: column;
  gap: 20px;
  position: relative;
  height: 100px;
  overflow: hidden;
}

.otherText {
  position: relative;
}

button {
  position: absolute;
  bottom: -5px;
  right: 0px;
  border: none;
  background-color: #fedd95;
}

.small-book {
  position: absolute;
  top: -20px;
  right: -15px;
  background-color: #f6ab09;
  padding: 15px;
  color: white;
  font-size: 14px;
  border-radius: 50%;
}
</style>
