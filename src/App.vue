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

    <Welcome/>

    <warnDaily v-if="test" />

  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import Welcome from './components/Welcome';
import warnDaily from './components/warnDaily';

export default {
  name: 'App',
  components: {
    Welcome,
    warnDaily,
  },
  data: () => ({
    test: true,
  }),
};
</script>
