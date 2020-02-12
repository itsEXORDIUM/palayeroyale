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
  props: {
    songTitle : String,
    songCover : String
  }
}
</script>