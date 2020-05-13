<template>
    <nav class="wrap" role="navigation">
        <button id="btn_menu" @click="openMenu($event)">
            <span class="btn"></span>
            <span>Menu</span>
        </button>
        <div id="mainMenu">
            <div class="wrap">
                <ul class="sideMenu">
                <ul class="socials">
                    <li class="twitter"><a href="http://twitter.com/palayeroyale" title="Follow the band on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                    <li class="instagram"><a href="http://instagram.com/palayeroyale" title="Follow the band on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                    <li class="facebook"><a href="http://www.facebook.com/PalayeRoyale" title="Follow the band on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
                    <li class="bandsintown"><a href="https://www.bandsintown.com/a/2390644-palaye-royale" title="Follow the band on bandsintown (New Window)" target="_blank"><span class="show-for-sr">bandsintown</span></a></li>
                    <li class="spotify"><a href="https://open.spotify.com/artist/0hAd6zwEgt9ILuMDY1prcI" title="Follow the band on Spotify (New Window)" target="_blank"><span class="show-for-sr">Spotify</span></a></li>
                </ul>
                </ul>
                <ul class="pages" @click="closeMenu()">
                <li @mouseover="changeBackground($event)" @mouseout="getActivePage()"><nuxt-link to="/">Home</nuxt-link></li>
                <li @mouseover="changeBackground($event)" @mouseout="getActivePage()"><nuxt-link to="/tourDates">Tour Dates</nuxt-link></li>
                <li @mouseover="changeBackground($event)" @mouseout="getActivePage()"><nuxt-link  to="/royalTelevision">Bastards Television</nuxt-link></li>
                <li @mouseover="changeBackground($event)" @mouseout="getActivePage()"><nuxt-link to="/news">News</nuxt-link></li>
                <li @mouseover="changeBackground($event)" @mouseout="getActivePage()"><a href="http://smarturl.it/HangOnToYourself" target="_blank" title="Go to the music page (New Window)" class="">Music</a></li>
                <li @mouseover="changeBackground($event)" @mouseout="getActivePage()"><nuxt-link to="/about">About</nuxt-link></li>
                </ul>
            </div>
            <img v-if="this.activepage === 'Home'" src="~/assets/img/menu/home.jpg" alt=""/>
            <img v-if="this.activepage === 'About'" src="~/assets/img/menu/about.jpg" alt=""/>
            <img v-if="this.activepage === 'News'" src="~/assets/img/menu/news.jpg" alt=""/>
            <img v-if="this.activepage === 'Bastards Television'" src="~/assets/img/menu/royaletelevision.jpg" alt=""/>
            <img v-if="this.activepage === 'Tour Dates'" src="~/assets/img/menu/tourdates.jpg" alt=""/>
            <img v-if="this.activepage === 'Music'" src="~/assets/img/menu/music.jpg" alt=""/>
        </div>

        <ul id="secondaryMenu">
            <li><a id="ticket_link" href="https://www.bandsintown.com/a/2390644-palaye-royale" class="action" title="Get tickets (New Window)" target="_blank"><span>Tickets</span></a></li>
            <li><a href="https://www.palayeroyale.store/" target="_blank" title="Get merch (New Window)" class="merch"><span>Get Merch</span></a></li>
            <li><button class="newsletter" @click="openPopin()"><span>Subscribe</span> <span class="show-for-sr">to the newsletter</span></button></li>
        </ul>
    </nav>
</template>

<script>
export default {
  data() {
        return {
          activepage: ''
        }
    },
  methods: {
      openPopin: function () {
          document.getElementById('popin_newsletter').classList.remove('fadeout');
          document.getElementById('popin_newsletter').classList.add('opened','fadein');
          document.body.classList.add('popin_open_small');
      },
      openMenu: function () {
          document.getElementById('mainMenu').classList.toggle('menuActive');
          var ticketLink = this.$el.querySelector('#ticket_link').parentNode;
          var sideMenu = this.$el.querySelector('.sideMenu');
          var secondaryMenu = this.$el.querySelector('#secondaryMenu');

          var text = this.$el.querySelector('span:not(.btn)').innerHTML;
          if (text === "Menu") {
                this.$el.querySelector('span:not(.btn)').innerHTML = "Close";
                ticketLink.remove();
                sideMenu.prepend(ticketLink);
                this.$el.querySelector('.btn').classList.add('toCross');
                 document.body.classList.add('popin_open');
            } else {
                this.$el.querySelector('span:not(.btn)').innerHTML = "Menu";
                ticketLink.remove();
                secondaryMenu.prepend(ticketLink);
                this.$el.querySelector('.btn').classList.remove('toCross');
                 document.body.classList.remove('popin_open');
            }        

        this.getActivePage();
      },
      getActivePage:function() {
        var pageActive = this.$el.querySelector('.nuxt-link-exact-active').textContent;
        this.activepage = pageActive;
      },
      closeMenu: function() {
          var ticketLink = this.$el.querySelector('#ticket_link').parentNode;
          var secondaryMenu = this.$el.querySelector('#secondaryMenu');
        document.querySelector('#mainMenu').classList.remove('menuActive');
        document.body.classList.remove('popin_open');
        document.querySelector('#btn_menu span:not(.btn)').innerHTML = "Menu";
        document.querySelector('#btn_menu span.btn').classList.remove('toCross');
        ticketLink.remove();
        secondaryMenu.prepend(ticketLink);
        },
    changeBackground: function(event) {
        var active = event.target.closest('a');
        if(active) {
            var background = active.textContent;
        }
        this.activepage = background;
    }
  }
}
</script>