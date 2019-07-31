<template>
  <v-app>
    <Nav />
    
    <Welcome />

    <warnDaily
      v-if="defaultWords.length" v-bind:defaultWords="defaultWords" />

  </v-app>
</template>

<script>
import axios from 'axios';
import Nav from './components/Nav';
import Welcome from './components/Welcome';
import warnDaily from './components/warnDaily';
import { key } from '../private';

export default {
  name: 'App',
  components: {
    Nav,
    Welcome,
    warnDaily,
  },
  data: () => ({
    test: true,
    defaultWords: [],
    searchWord: '',
  }),
  methods: {
    fetchSynonyms(e) {
      console.log('Search the Thing: ')
      console.log(this.searchWord)
    }
  },
  created() {
    axios.get(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/day${key}`)
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
