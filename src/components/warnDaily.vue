<template>
  <section>
    <v-alert
        text
        dense
        color="teal"
        icon="mdi-clock-fast"
        border="left"
      >
      No Search has been entered: <br/>
      DISPLAYING: Words of the day
    </v-alert>
    <WordList/>
  </section>
</template>

<script>
import WordList from './WordList/WordList';

export default {
  name: 'App',
  components: {
    WordList,
  },
  data: () => ({
    //
  }),
};
</script>