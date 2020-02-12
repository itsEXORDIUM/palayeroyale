<template>
    <div id="latest_videos">
        <h2>Latest Videos</h2>
        {{firstVideo}}
        {{secondVideo}}
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