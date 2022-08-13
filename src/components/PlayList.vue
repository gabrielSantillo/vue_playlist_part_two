<template>
    <div>
        <h1>Playlist</h1>
        <p ref="music_play_list"></p>
    </div>
</template>

<script>
    export default {
        methods: {
            handle_music_clicked(name) {
                this.$refs[`music_play_list`][`innerText`] += name;
            }
        },
        mounted () {
            this.$root.$on(`music_clicked`, this.handle_music_clicked);
        },
    }
</script>

<style scoped>

</style>