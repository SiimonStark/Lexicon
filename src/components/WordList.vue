<template>
  <v-expansion-panels focusable v-if="defaultWords">
    <v-expansion-panel
      v-for="(item) in defaultWords"
      :key="item.meta.uuid"
    >
      <v-expansion-panel-header>
        {{ item.hwi.hw.toUpperCase() }}
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
  props: ['defaultWords'],
  data: () => ({
    //
  }),
  methods: {
  },
};
</script>
