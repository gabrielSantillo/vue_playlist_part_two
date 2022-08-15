<template>
  <div>
    <h1>Playlist</h1>
    <div ref="music_play_list" class="music_play_list"></div>
  </div>
</template>

<script>
export default {
  methods: {
    handle_music_clicked(object) {
      this.$refs[`music_play_list`].insertAdjacentHTML(`beforeend`, `
      <p class="music_name" song_id="${object[`song_id`]}">${object[`title`]}</p>
      `);
    },
  },
  mounted() {
    this.$root.$on(`music_clicked`, this.handle_music_clicked);
  },
};
</script>

<style scoped>
.music_play_list {
    cursor: pointer;
}
</style>
