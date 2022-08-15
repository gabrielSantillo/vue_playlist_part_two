<template>
  <div>
    <p ref="playing_now"></p>
  </div>
</template>

<script>
export default {
  methods: {
    music_playing_now(name) {
      this.$refs[`playing_now`][`innerHTML`] = name;
    },
  },

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
