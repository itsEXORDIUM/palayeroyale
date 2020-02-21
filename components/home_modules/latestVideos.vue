<template>
    <div id="latest_videos" class="bloc_home">
        <h2 class="title_home">Latest Videos</h2>
        <ul>
          <li>
            <a :href="firstVideo.video_url" :title="`See the video for ${firstVideo.video_title} on Youtube (New Window)`" target="_blank">
              <img :src="firstVideo.video_thumbnail" :alt="firstVideo.video_title"/>
            </a>
          </li>
          <li>
            <a :href="secondVideo.video_url" :title="`See the video for ${secondVideo.video_title} on Youtube (New Window)`" target="_blank">
              <img :src="secondVideo.video_thumbnail" :alt="secondVideo.video_title"/>
            </a>
          </li>
        </ul>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    firstVideo : Object,
    secondVideo : Object
  }
}
</script>