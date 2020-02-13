<template>
    <div id="latest_song">
        <h2 class="show-for-sr">Latest Song</h2>
        <div class="content">
          <h3>Listen to {{songTitle}}</h3>
          <img :src="songCover" alt=""/>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  components: {
  },
  props: {
    songTitle : String,
    songCover : String
  }
}
</script>