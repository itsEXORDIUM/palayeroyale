<template>
    <div id="tour_dates" class="bloc_home wrap">
      <div class="content">
        <h2 v-if="home" class="title_home">Tour Dates</h2>
        <h1 class="title_home" v-else>Tour Dates</h1>
        <tourDatesPosts :tourDates="tourDates"/>

        <div class="big_action">
          <nuxt-link v-if="home" to="/tourDates" class="action"><span>More Dates</span></nuxt-link>
          <button class="action" v-else><span>More Dates</span></button>
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
    tourDates: Array,
    home: Boolean
  },
  mounted() {
    this.$el.querySelector('.title_home').classList.add('fadein','delay');
    this.$el.querySelector('.big_action').classList.add('fadein','delay_two');
  }
}
</script>