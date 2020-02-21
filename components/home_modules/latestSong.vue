<template>
    <div id="latest_song">
        <h2 class="show-for-sr">Latest Song</h2>
        <div class="content">
          <h3>Listen to or buy {{songTitle}}</h3>
          <img :src="songCover" alt=""/>
        </div>
        <ul class="links">
          <li class="deezer"><a :href="deezer" :title="`Listen to ${songTitle} on Deezer (New Window)`" target="_blank"><span class="show-for-sr">Deezer</span></a></li>
          <li class="youtube_music"><a :href="youtube_music" :title="`Listen to ${songTitle} on Youtube Music (New Window)`" target="_blank"><span class="show-for-sr">Youtube Music</span></a></li>
          <li class="spotify"><a :href="spotify" :title="`Listen to ${songTitle} on Spotify (New Window)`" target="_blank"><span class="show-for-sr">Spotify</span></a></li>
          <li class="google_play"><a :href="google_play" :title="`Buy ${songTitle} on Google Play (New Window)`" target="_blank"><span class="show-for-sr">Google Play</span></a></li>
          <li class="amazon_music"><a :href="amazon_music" :title="`Buy ${songTitle} on Amazon Music (New Window)`" target="_blank"><span class="show-for-sr">Amazon Music</span></a></li>
          <li class="itunes"><a :href="itunes" :title="`Buy ${songTitle} on Itunes (New Window)`" target="_blank"><span class="show-for-sr">Itunes</span></a></li>
        </ul>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  components: {
  },
  props: {
    songTitle : String,
    songCover : String,
    deezer: String,
    spotify: String,
    youtube_music: String,
    google_play: String,
    amazon_music: String,
    itunes: String
  }
}
</script>