<template>
  <div>
    <p ref="playing_now"></p>
  </div>
</template>

<script>
export default {
  methods: {
    /* this function has the ability to handle the information received from the emitter by printing the name of the music onto the section */
    music_playing_now(name) {
        /* getting the div by its reference and printing the name of the chosen music to be added to the playing now section */
      this.$refs[`playing_now`][`innerHTML`] = name;
    },
  },
/* listening the emitter that created the custom function music_playing_clicked and calling to a new function to handle the information passed by the emitter */
  mounted() {
    this.$root.$on(`music_playing_clicked`, this.music_playing_now);
  },

  data() {
    return {
      now_playing_in_on: false,
    };
  },
};
</script>

<style scoped></style>
