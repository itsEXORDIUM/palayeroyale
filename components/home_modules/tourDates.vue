<template>
    <div id="tour_dates" class="bloc_home wrap">
      <div class="content">
        <h2 class="title_home">Tour Dates</h2>
        <tourDatesPosts :tourDates="tourDates"/>

        <div class="big_action">
          <nuxt-link to="/tourDates" class="action"><span>More Dates</span></nuxt-link>
        </div>
        
      </div>
      <img :src="tourPoster" alt=""/>
    </div>
</template>

<script>
import tourDatesPosts from '~/components/post_types/tourDates'

export default {
  components: {
    tourDatesPosts
  },
  props: {
    tourPoster: String,
    tourDates: Array
  }
}
</script>