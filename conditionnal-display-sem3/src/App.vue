<script setup>
import { ref } from 'vue'

// Part 1

const userNotConnected = ref(true)

// Part 2
const userLiked = ref(true)

// Part 3
const wallet = ref(0)

const addOneEuro = () => {
  wallet.value++
}
const addFiveEuros = () => {
  wallet.value = wallet.value + 5
}

// Part 4

const usersList = [
  {
    id: 23,
    gender: 'female',
    firstname: 'Emily',
    lastname: 'Parker',
    age: 24,
    account: {
      premium: true,
      avatar: {
        url: 'https://res.cloudinary.com/lereacteur-apollo/image/upload/v1706536025/RNCP31114/cours-vue/exos-sem-3/conditionnal-display-emily_py1pu1.jpg',
      },
    },
  },
  {
    id: 54,
    gender: 'male',
    firstname: 'Marcus',
    lastname: 'Bennett',
    age: 38,
    account: {
      premium: false,
    },
  },
]
</script>

<template>
  <h1>Conditionnal display</h1>

  <section>
    <div v-if="userNotConnected">
      <button @click="userNotConnected = !userNotConnected">S'inscrire</button>
      <button @click="userNotConnected = !userNotConnected">Se connecter</button>
    </div>
    <div v-else>
      <button @click="userNotConnected = true">Se déconnecter</button>
    </div>
  </section>

  <section>
    <font-awesome-icon
      :icon="['fas', 'thumbs-up']"
      v-if="userLiked"
      @click="userLiked = !userLiked"
    />
    <font-awesome-icon :icon="['fas', 'thumbs-down']" v-else @click="userLiked = !userLiked" />
  </section>

  <section>
    <p v-if="wallet > 30">Ca y est je suis riche !!</p>
    <p v-else-if="wallet < 30 && wallet > 10">Yes ! Plus de 10 euros !</p>
    <p v-else-if="wallet === 1">Mon premier euro !</p>
    <p v-else-if="wallet === 0">Mon porte-monnaie est vide</p>

    <p>{{ wallet }}</p>
    <button @click="addOneEuro">Ajouter 1€</button>
    <button @click="addFiveEuros">Ajouter 5€</button>
  </section>

  <section class="cards">
    <div v-for="user in usersList" :key="user.id">
      <img v-if="user.account.premium" :src="user.account.avatar.url" alt="" />
      <p v-else><font-awesome-icon :icon="['fas', 'user']" /></p>

      <div>
        <p>{{ user.firstname }}</p>
        <p>{{ user.lastname }}</p>
        <p>{{ user.age }} ans</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.cards {
  /* border: 1px black solid; */
  display: flex;
}
.cards > div {
  /* border: 1px solid red; */
  display: flex;
}

.cards img {
  height: 30px;
  width: 30px;
}
</style>
