<script setup>
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
  <div>
    <div v-for="user in usersList" :key="user.id">
      <img v-if="user.account.avatar" :src="user.account.avatar.url" alt="" />
      <font-awesome-icon :icon="['fas', 'user']" v-if="!user.account.avatar" />

      <div>
        <p>{{ user.firstname }}</p>
        <p>{{ user.lastname }}</p>
        <p>{{ user.age }} ans</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
img {
  height: 30px;
  width: 30px;
  object-fit: cover;
}
</style>
