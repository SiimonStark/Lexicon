<template>
  <v-expansion-panels focusable v-if="words">
    <v-expansion-panel
      v-for="(item) in words"
      :key="item.meta.uuid"
    >
      <v-expansion-panel-header>
        <i v-if="isFavorite()" class="fas fa-heart heart-red"></i>
        <i v-else class="far fa-heart heart-gray"></i>
        <span>{{ item.hwi.hw.toUpperCase() }}</span>
      </v-expansion-panel-header>
      <v-expansion-panel-content>
        <h4>Definitions:</h4>
          <p
            v-for="(item, ind) in item.shortdef" :key="ind">
            - {{item}},
          </p>
        <h4>Possible Synonyms:</h4>
        <p>
          <span
            v-on:click="sendClicked"
            v-for="(item, ind) in item.meta.syns.flat()" :key="ind">
            {{item}},
          </span>
        </p>
      </v-expansion-panel-content>
    </v-expansion-panel>
  </v-expansion-panels>
</template>
<script>

export default {
  name: 'WordList',
  props: ['words'],
  data: () => ({
    //
  }),
  methods: {
    isFavorite(e) {
      return true;
    },
    sendClicked(e) {
      this.$emit('input-search', e.target.innerText);
    }
  },
};
</script>
<style lang="scss" scoped>
  .heart-red {
    color: red;
  }
  .heart-gray {
    color: gray;
  }
</style>
