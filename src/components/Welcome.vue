<template>
  <section class="welcome-img">
    <v-img
      src="https://cdn.dribbble.com/users/1162077/screenshots/3895488/writer.gif"
      lazy-src="https://icon-library.net/images/spinner-icon-gif/spinner-icon-gif-29.jpg"
      aspect-ratio="1"
      class="lighten-4 welcome-img"
      max-width="500"
      max-height="300"
    ></v-img>

    <div>
      <h2 class="display-1 text-center">Welcome to Lexicon!</h2>
      <p class="subtitle-1 text-center">
        We invite you to challenge your creative writing skills<br />
        Search a word above to get a list of synonyms
      </p>
    </div>
  </section>
</template>
<script>
export default {
  name: 'Welcome',
};
</script>
<style lang="scss" scoped>
  .welcome-img {
    margin: auto;
  }
</style>