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
    /* this function has the ability to handle the information received from the emitter */
    handle_music_clicked(object) {
        /* getting the div from by its reference and adding the name of the music that was clicked */
      this.$refs[`music_play_list`].insertAdjacentHTML(
        `beforeend`,
        `
      <p class="music_name" song_id="${object[`song_id`]}">${
          object[`title`]
        }</p>
      `
      );
    },
    /* this function is called after the user chose the music to listen */
    music_being_played(details) {
        /* change the value of the variable to true */
      this.is_music_here = true;
      /* get name of the music by its text */
      let music_name = details[`target`][`innerHTML`];
      /* creating a custom event, called music_playing_clicked and passing the name of the music to the listener */
      this.$root.$emit(`music_playing_clicked`, music_name);
    },
  },
  mounted() {
    /* listening the emitter that created the custom function music_clicked and calling to a new function to handle the information passed by the emitter */
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
