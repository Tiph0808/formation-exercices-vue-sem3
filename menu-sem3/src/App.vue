<script setup>
import { ref, computed } from 'vue'
import articles from './assets/data.json'
console.log(articles)

const selectedArticle = ref(null)

const handleClick = (article) => {
  selectedArticle.value = article
}

const averageRate = computed(() => {
  let total = 0
  for (let i = 0; i < selectedArticle.value.rates.length; i++) {
    total = total + selectedArticle.value.rates[i]
  }
  return total / selectedArticle.value.rates.length
})
</script>

<template>
  <header>
    <button v-for="article in articles" :key="article.id" @click="handleClick(article)">
      {{ article.title }}({{ article.category }})
    </button>
  </header>
  <main>
    <p v-if="!selectedArticle">Faites votre choix</p>
    <div v-else-if="selectedArticle.category === 'livre'">
      <p>{{ selectedArticle.synopsis }}</p>
      <p v-if="selectedArticle.author">{{ selectedArticle.author }}</p>
      <p>{{ averageRate }}</p>
      <p v-if="selectedArticle.numberOfPage < 250">Petit Livre</p>
    </div>
    <div v-else-if="selectedArticle.category === 'article'">
      <p>{{ selectedArticle.content }}</p>
      <p v-if="selectedArticle.author">{{ selectedArticle.author.name }}</p>
      <p>{{ averageRate }}</p>
    </div>
  </main>
</template>

<style scoped></style>
