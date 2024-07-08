<template>
  <v-container class="fill-height">
    <v-responsive class="align-centerfill-height mx-auto" max-width="900">
      <v-btn @click="shuffle">Maišyti</v-btn>
      <LetterGrid :letters="letters" />
    </v-responsive>
  </v-container>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import LetterGrid from './LetterGrid.vue';
import { ref } from 'vue';

const rndKey = ref(Math.random());

const words = ref(['akis', 'ranka', 'ausis', 'nosis']);

const letters = computed(() => words.value
  .reduce((letters, word) => letters.concat(word.split('')), [])
  .map(letter => ({ letter, sort: Math.random() }))
  .sort((a, b) => a.sort - b.sort + rndKey.value)
  .map(({ letter }) => letter));

function shuffle() {
  console.log('shuffle')
  rndKey.value = Math.random();
  words.value = words.value.filter(w => w !== 'akis');
}

//
</script>
