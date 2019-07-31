<template>
  <v-app-bar app dark class="blue accent-1">
    <v-toolbar-title class="headline text-uppercase">
      Lexicon
    </v-toolbar-title>
    <v-spacer></v-spacer>

    <!-- <v-autocomplete
      label="Search Synonyms"
      v-model="searchWord"
      class="mt-5"
      v-on:change="fetchSynonyms"
    ></v-autocomplete> -->

    <v-text-field
      filled
      class="mt-6 font-weight-medium subtitle-2"
      v-model="searchWord"
      v-on:change="handleSearch"
      color="blue-grey lighten-2"
      label="Search Synonyms"
    ></v-text-field>


    <v-btn icon v-on:click="handleSearch">
      <v-icon>mdi-magnify</v-icon>
    </v-btn>

    <v-btn icon
      :disabled="!searchWord"
      color="white darken-3"
      @click="searchWord = ''"
    >
      <v-icon right>mdi-close-circle</v-icon>
    </v-btn>

  </v-app-bar>
</template>
<script>
export default {
  name: 'Nav',
  props: ['defaultWords'],
  data: () => ({
    searchWord: '',
  }),
  methods: {
    handleSearch() {
      this.$emit('input-search', this.searchWord);
    },
    clearSearch() {
      this.searchWord = '';
    }
  },
};
</script>