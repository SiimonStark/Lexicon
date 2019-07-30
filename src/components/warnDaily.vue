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
    <WordList v-bind:defaultWords="defaultWords" />
  </section>
</template>

<script>
import WordList from './WordList';

export default {
  name: 'warnDaily',
  props: ['defaultWords'],
  components: {
    WordList,
  },
  data: () => ({
    //
  }),
};
</script>
