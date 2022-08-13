<template>
  <div>
    <section>
      
      <article v-for="song in songs" :key="song[`song_id`]">
        <p>{{ song[`title`] }}</p>
        <p>{{ song[`artist`] }}</p>
        <img
          :src="song[`img_url`]"
          alt=""
          @click="highlight_music"
          :song_id="song[`song_id`]"
        />
      </article>
    </section>
    <div v-if="song_being_listened === false">
      <h2>Pick a song</h2>
    </div>
    
  </div>
</template>

<script>
export default {
  
  methods: {
    
    highlight_music(details) {
      
      let song_id = details[`target`].getAttribute(`song_id`);
      
      for(let i = 0; i < this.songs.length; i++) {
        if(this.songs[i][`song_id`] === song_id) {
           let chosen_music_name = this.songs[i][`name`];
           this.$root.$emit(`music_clicked`, chosen_music_name);
        }
      }
    },
  },

  data() {
    return {
      /* this is a variable that starts as false so the h2 tag can be displayed in the screen an alert the user to pick a song */
      song_being_listened: false,
      /* array with 3 objects inside. Each object contain a title, band name, song id and an image that representes the song */
      songs: [
        {
          title: `In the End`,
          artist: `Linkin Park`,
          song_id: `01`,
          img_url: `https://upload.wikimedia.org/wikipedia/en/3/3f/LinkinParkIntheEnd.jpg`,
        },

        {
          title: `Breaking the Habit`,
          artist: `Linkin Park`,
          song_id: `02`,
          img_url: `https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/da680c00-9fa8-4307-990a-993c02f4e879/dbv4fm-d88459c0-39a4-48e9-ab63-c48a1573ed6f.jpg/v1/fill/w_474,h_416,q_75,strp/linkin_park_breaking_the_habit_by_shadowsweeper_dbv4fm-fullview.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7ImhlaWdodCI6Ijw9NDE2IiwicGF0aCI6IlwvZlwvZGE2ODBjMDAtOWZhOC00MzA3LTk5MGEtOTkzYzAyZjRlODc5XC9kYnY0Zm0tZDg4NDU5YzAtMzlhNC00OGU5LWFiNjMtYzQ4YTE1NzNlZDZmLmpwZyIsIndpZHRoIjoiPD00NzQifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6aW1hZ2Uub3BlcmF0aW9ucyJdfQ.APCYVvCVG4HGMa7hovb5xjli9wy4leW7beKUunhjuaI`,
        },

        {
          title: `Numb`,
          artist: `Linkin Park`,
          song_id: `03`,
          img_url: `https://m.media-amazon.com/images/I/51A9bZDvTkL._AC_.jpg`,
        },
      ],
    };
  },
};
</script>

<style scoped>
section {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  column-gap: 20px;
}

img {
  width: 250px;
  height: 250px;
  cursor: pointer;
}

</style>