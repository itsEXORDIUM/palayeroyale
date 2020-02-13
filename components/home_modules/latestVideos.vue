<template>
    <div id="latest_videos" class="bloc_home">
        <h2>Latest Videos</h2>
        <ul>
          <li>
            <a :href="firstVideo.video_url">
              <img :src="firstVideo.video_thumbnail" alt=""/>
            </a>
          </li>
          <li>
            <a :href="secondVideo.video_url">
              <img :src="secondVideo.video_thumbnail" alt=""/>
            </a>
          </li>
        </ul>
        <p>Ajouter video title dans le wordpress</p>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    firstVideo : Array,
    secondVideo : Array
  }
}
</script>