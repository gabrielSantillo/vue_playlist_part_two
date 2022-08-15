<template>
  <div>
    <div
      ref="music_play_list"
      class="music_play_list"
      @click="music_being_played"
    ></div>
    <div v-if="is_music_here === true">
      <h1>Playing now</h1>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    handle_music_clicked(object) {
      this.$refs[`music_play_list`].insertAdjacentHTML(
        `beforeend`,
        `
      <p class="music_name" song_id="${object[`song_id`]}">${
          object[`title`]
        }</p>
      `
      );
    },

    music_being_played(details) {
      this.is_music_here = true;
      let music_name = details[`target`][`innerHTML`];
      this.$root.$emit(`music_playing_clicked`, music_name);
    },
  },
  mounted() {
    this.$root.$on(`music_clicked`, this.handle_music_clicked);
  },

  data() {
    return {
      is_music_here: false,
    };
  },
};
</script>

<style scoped>
.music_play_list {
  cursor: pointer;
}
</style>
