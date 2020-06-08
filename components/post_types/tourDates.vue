<template>
    <div id="dates" class="">
      <div class="tour_line" v-for="(date, index) in tourDates" :key="index">
        <div class="date">
          <span class="weekday">{{date.acf.tour_date.week_day}}</span>
          <span class="day">{{date.acf.tour_date.date}}</span>
        </div>
        <div class="place_city">
          <span class="place">{{date.acf.tour_date.place}}</span>
          <span class="city">{{date.acf.tour_date.city}}</span>
          <a :href="date.acf.tour_date.concert_link" :title="`See the concert in ${date.acf.tour_date.city} on the ticket Website ( New Window )`" target="_blank"><span class="show-for-sr">See the concert on the ticket Website</span></a>
        </div>
        <div class="guests hide-for-phone">
          <span v-if="date.acf.tour_date.guest">With {{date.acf.tour_date.guest}}</span>
        </div>
        <ul class="tickets">
          <li><a :href="date.acf.tour_date.ticket_link" class="small_action action" target="_blank"><span>Tickets</span></a></li>
          <li class="hide-for-phone"><a :href="date.acf.tour_date.vips_link" class="small_action action" target="_blank"><span>VIPS</span></a></li>
          <li><a :href="date.acf.tour_date.rsvp_link" class="small_action action" target="_blank"><span>RSVP</span></a></li>
        </ul>
      </div>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    tourPoster: String,
    tourDates: Array
  }
}
</script>