<script setup>
const props = defineProps({
  selection: Object,
  average: Number,
})
</script>
<template>
  <section class="content-card">
    <h2>{{ selection.title }}</h2>
    <div class="text">
      <p v-for="paragraph in selection.synopsis.split('\n')">{{ paragraph }}</p>
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

.text {
  border: 1px solid gray;
  display: flex;
  flex-direction: column;
  gap: 20px;
  height: 100px;
  overflow: hidden;
}
</style>
