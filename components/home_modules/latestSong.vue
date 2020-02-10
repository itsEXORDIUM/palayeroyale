<template>
    <div id="latest_song">
        <h2>Latest Song</h2>
        {{songTitle}}
        {{songCover}}
    </div>
</template>

<script>
import axios from 'axios'

export default {
  components: {
  },
  data() {
    return {
      latestSong: [],
      songTitle: '',
      songCover: ''
    }
  },
  mounted() {
    // Get Home Page Data
    axios.get('http://51.15.241.193/wp-json/wp/v2/pages/10')
      .then(response => {
          this.latestSong = response.data;
          this.songTitle = response.data.acf.song_title;
          this.songCover = response.data.acf.song_cover;
      })
  }
}
</script>