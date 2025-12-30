<script setup>
import { ref, computed } from 'vue'

const users = ref([
  {
    id: 1,
    name: 'Sarah',
    age: 30,
    books: [
      {
        title: 'Lorem ipsum',
        numOfPages: 352,
      },
      {
        title: 'Totam perspiciatis',
        numOfPages: 3057,
      },
      {
        title: 'Distin lipsum',
        numOfPages: 120,
      },
    ],
  },
  {
    id: 2,
    name: 'Olivier',
    age: 14,
    books: [
      {
        title: 'Distinctio',
        numOfPages: 873,
      },
      {
        title: 'Totam perspiciatis',
        numOfPages: 3057,
      },
    ],
  },
  {
    id: 3,
    name: 'Sam',
    age: 42,
    books: [
      {
        title: 'Numquam volup',
        numOfPages: 1309,
      },
      {
        title: 'Lorem ipsum',
        numOfPages: 479,
      },
      {
        title: 'Ipsum soluta',
        numOfPages: 1468,
      },
      {
        title: 'Voluptatibus',
        numOfPages: 3801,
      },
    ],
  },
])

const numberOfBooks = computed(() => {
  let total = 0
  for (let i = 0; i < users.value.length; i++) {
    total = total + users.value[i].books.length
  }
  return total
})

console.log(numberOfBooks.value)

const numberOPages = computed(() => {
  let total = 0
  for (let i = 0; i < users.value.length; i++) {
    for (let j = 0; j < users.value[i].books.length; j++) {
      total = total + users.value[i].books[j].numOfPages
    }
  }
  return total
})

console.log(numberOPages.value)

const addUser = () => {
  users.value.push({
    id: 4,
    name: 'John',
    age: 33,
    books: [
      {
        title: 'Lorem ipsum',
        numOfPages: 352,
      },
      {
        title: 'Totam perspiciatis',
        numOfPages: 3057,
      },
    ],
  })
}
</script>
<template>
  <p>Le groupe de lecture compte {{ users.length }} membres</p>
  <p>
    A eux {{ users.length }}, ils ont lu {{ numberOfBooks }} livres pour un total de
    {{ numberOPages }} pages.
  </p>
  <button @click="addUser">Ajouter un utilisateur</button>
</template>
<style scoped></style>
