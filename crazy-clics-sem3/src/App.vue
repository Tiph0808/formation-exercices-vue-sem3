<script setup>
//Import des differents composants
import Part1 from './components/Part1.vue'
import Part2 from './components/Part2.vue'
import Part3 from './components/Part3.vue'

// au clic sur l'un des boutons dans les composants enfants, l'utilisateur ne doit pas avoir besoin de rafraichir son navigateur pour voir le resultat, on a donc besoin que ce resultat soit une valeur reactive
// au click dans le composant enfant, un event sera emis le composant parent l'ecoutera et modifiera cett valeur reactive

//  j'importe ref :
import { ref } from 'vue'

// Je crée ma valeur reactive RESULT

const result = ref('') // on initialise avec une str vide

// PARTIE 1

//Declaration de la fonction declenchée a l'écoute de l'evenement 'correctTheWord'
const handleWordCorrection = (word) => {
  result.value = word.charAt(0).toUpperCase() + word.slice(1).toLowerCase()
}
// Autre méthode, avec une boucle :) :
// const handleWordCorrection = (word) => {
//   let correctedWord = ''
//   for (let i = 0; i < word.length; i++) {
//     if (i === 0) {
//       correctedWord = correctedWord + word[i].toUpperCase()
//     } else {
//       correctedWord = correctedWord + word[i].toLowerCase()
//     }
//   }
//   result.value = correctedWord
// }

// PARTIE 2
// import des donnees necessaires du fichier data.js
import { colorsList } from './utils/data.js'
// console.log(colorsList)

const getRandomColor = () => {
  const randomIndex = Math.floor(Math.random() * colorsList.length) // ici Math.random selectionne un nombre aleatoire entre 0 et 9  (ex: 2,2566), Mat.floor arrondi ce nombre a l'entier naturel inferieur (2,2566 => 2)
  result.value = colorsList[randomIndex]
}

// PARTIE 3

const convertNumberToCm = (number) => {
  result.value = ` ${number} km = ${number * 100000} cm`
}
</script>

<template>
  <main>
    <h1>Crazy clics v2</h1>
    <section>
      <div>
        <div>
          <Part1 @correctTheWord="handleWordCorrection" />
        </div>
        <div>
          <Part2 @getRandomColor="getRandomColor" />
        </div>
        <div>
          <Part3 @convertToCm="convertNumberToCm" />
        </div>
      </div>
      <div>
        <h2>Le resultat</h2>
        <p>{{ result }}</p>
      </div>
    </section>
  </main>
</template>

<style scoped></style>
