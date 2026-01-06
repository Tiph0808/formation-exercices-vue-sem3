<script setup>
const props = defineProps({
  selection: Object,
  average: Number,
})
</script>

<template>
  <section class="content-card">
    <h2>{{ selection.title }}</h2>

    <p v-for="paragraph in selection.content.split('\n')">{{ paragraph }}</p>

    <p class="author" v-if="selection.author">{{ selection.author.name }}</p>
    <div class="rates">
      <font-awesome-icon :icon="['fas', 'thumbs-up']" />
      <span>{{ average }}</span>
    </div>
  </section>
</template>
<style scoped>
@import '../assets/style.css';
</style>
