<template>
    <div id="tour_dates">
        <h2>Tour Dates</h2>
        {{tourPoster}}
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    tourPoster: String
  }
}
</script>