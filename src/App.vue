<template>
  <v-app>
    <Nav v-on:input-search="searchSynonyms" />

    <Welcome />

    <warnDaily
      v-if="!foundWords.length" v-bind:defaultWords="defaultWords"
      v-on:input-search="searchSynonyms" />

    <WordList
      v-if="foundWords.length"
      v-bind:words="foundWords"
      v-on:input-search="searchSynonyms" />

  </v-app>
</template>

<script>
import axios from 'axios';
import Nav from './components/Nav.vue';
import Welcome from './components/Welcome.vue';
import warnDaily from './components/warnDaily.vue';
import WordList from './components/WordList.vue';
// import { key } from '../private';
require('dotenv').config();

export default {
  name: 'App',
  components: {
    Nav,
    Welcome,
    warnDaily,
    WordList,
  },
  data: () => ({
    test: true,
    defaultWords: [],
    searchWord: '',
    foundWords: [],
  }),
  methods: {
    searchSynonyms(word) {
      this.searchWord = word;
      word !== '' ? this.fetchSynonyms(word) : null;
    },
    fetchSynonyms(word) {
      axios.get(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/${word}?key=${process.env.VUE_APP_SECRET}`)
        .then(res => this.foundWords = res.data)
        .catch(err => console.log(err));
    },
  },
  created() {
    axios.get(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/day?key=${process.env.VUE_APP_SECRET}`)
      .then(res => this.defaultWords = res.data)
      .catch(err => console.log(err));
  },
};
</script>
<style lang="scss" scoped>
  #input-5 {
    font-size: 26px;
  }
</style>
