<template>
    <div id="tour_dates" class="bloc_home wrap">
      <div class="content">
        <h2 v-if="home" class="title_home">Tour Dates</h2>
        <h1 class="" v-else>Tour Dates</h1>
        <tourDatesPosts :tourDates="tourDates"/>

        <div class="big_action">
          <nuxt-link v-if="home" to="/tourDates" class="action"><span>More Dates</span></nuxt-link>
          <button class="" v-else><span>More Dates</span></button>
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
    this.apparitions();
  },
  methods: {
      apparitions: function() {
        if(this.$el.querySelector('h1')) {
          this.$el.querySelector('h1').classList.add('title_home','fadein','delay');
        }

        if(this.$el.querySelector('.big_action button')) {
          this.$el.querySelector('.big_action button').classList.add('action','fadein','delay_two');
        }
          
        if(this.$el.querySelector('#dates')) {
          this.$el.querySelector('#dates').classList.add('dates','fadein','delay_two');
        }
      }
  }
}
</script>