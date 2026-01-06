<script setup>
import data from '../assets/data.json'
const props = defineProps({
  data: Array,
})

const emit = defineEmits(['elementSelected'])
</script>

<template>
  <header>
    <div>
      <button v-for="element in data" :key="element.id" @click="emit('elementSelected', element)">
        <span>{{ element.title }} </span>({{ element.category }})
      </button>
    </div>
  </header>
</template>

<style scoped>
header {
  /* border: 1px solid green; */
  height: 150px;
  width: 1000px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

header > div {
  /* border: 1px solid red; */
  display: flex;
  gap: 30px;
  justify-content: center;
  align-items: center;
}

button {
  padding: 10px 15px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  background-color: white;
  border: 3px solid #f6ab09;
  border-radius: 5px;
}

button span {
  color: #f6ab09;
  padding-right: 5px;
  font-weight: bold;
}
</style>
