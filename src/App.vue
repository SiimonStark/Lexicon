<template>
  <v-app>
    <v-app-bar app dark class="blue accent-1">
      <v-toolbar-title class="headline text-uppercase">
        Lexicon
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <v-autocomplete
        label="Synonyms"
        :items="components"
      ></v-autocomplete>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-filter</v-icon>
      </v-btn>
    </v-app-bar>

    <Welcome />

    <warnDaily
      v-if="defaultWords.length" v-bind:defaultWords="defaultWords" />

  </v-app>
</template>

<script>
import axios from 'axios';
import Welcome from './components/Welcome';
import warnDaily from './components/warnDaily';
import { key } from '../private';

export default {
  name: 'App',
  components: {
    Welcome,
    warnDaily,
  },
  data: () => ({
    test: true,
    defaultWords: [],

  }),
  methods: {

  },
  created() {
    axios.get(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/day${key}`)
      .then(res => this.defaultWords = res.data)
      .catch(err => console.log(err));
  },
};
</script>
