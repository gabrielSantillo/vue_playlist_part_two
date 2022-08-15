<template>
  <div>
    <h1>Playlist</h1>
    <div ref="music_play_list"></div>
  </div>
</template>

<script>
export default {
  methods: {
    handle_music_clicked(name) {
      this.$refs[`music_play_list`].insertAdjacentHTML(`beforeend`, `
      <p>${name}</p>
      `);
    },
  },
  mounted() {
    this.$root.$on(`music_clicked`, this.handle_music_clicked);
  },
};
</script>

<style scoped></style>
