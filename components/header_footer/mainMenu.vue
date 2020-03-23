<template>
    <div id="mainMenu">
      <div class="wrap">
        <ul class="sideMenu">
          <li v-if="!ticketLink"><a id="ticket_link" href="https://www.bandsintown.com/a/2390644-palaye-royale" class="action" title="Get tickets (New Window)" target="_blank"><span>Tickets</span></a></li>
          <ul class="socials">
            <li class="twitter"><a href="http://twitter.com/palayeroyale" title="Follow the band on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
            <li class="instagram"><a href="http://instagram.com/palayeroyale" title="Follow the band on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
            <li class="facebook"><a href="http://www.facebook.com/PalayeRoyale" title="Follow the band on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
            <li class="bandsintown"><a href="https://www.bandsintown.com/a/2390644-palaye-royale" title="Follow the band on bandsintown (New Window)" target="_blank"><span class="show-for-sr">bandsintown</span></a></li>
            <li class="spotify"><a href="https://open.spotify.com/artist/0hAd6zwEgt9ILuMDY1prcI" title="Follow the band on Spotify (New Window)" target="_blank"><span class="show-for-sr">Spotify</span></a></li>
          </ul>
        </ul>
        <ul class="pages" @click="closeMenu()">
          <li><nuxt-link to="/">Home</nuxt-link></li>
          <li><nuxt-link to="/tourDates">Tour Dates</nuxt-link></li>
          <li><nuxt-link to="/royalTelevision">Bastards Television</nuxt-link></li>
          <li><nuxt-link to="/news">News</nuxt-link></li>
          <li><a href="#">Music</a></li>
          <li><nuxt-link to="/about">About</nuxt-link></li>
        </ul>
      </div>
      <img :src="`/_nuxt/assets/img/menu/${backgroundMenu}.jpg`" alt=""/>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    backgroundMenu: String,
    ticketLink: Boolean
  },
  methods: {
    closeMenu: function() {
      document.querySelector('#mainMenu').classList.remove('menuActive');
      document.body.classList.remove('popin_open');
      document.querySelector('#btn_menu span:not(.btn)').innerHTML = "Menu";
      document.querySelector('#btn_menu span.btn').classList.remove('toCross');
    }
  }
}
</script>