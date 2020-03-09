<template>
    <nav class="wrap" role="navigation">
        <button id="btn_menu" @click="openMenu($event)">
            <span class="btn"></span>
            <span>Menu</span>
        </button>
        <mainMenu :backgroundMenu="backgroundMenu"/>

        <ul id="secondaryMenu">
            <li><a href="https://www.bandsintown.com/a/2390644-palaye-royale" class="action" title="Get tickets (New Window)" target="_blank"><span>Tickets</span></a></li>
            <li><a href="https://www.palayeroyale.store/" target="_blank" title="Get merch (New Window)" class="merch"><span>Get Merch</span></a></li>
            <li><button class="newsletter" @click="openPopin()"><span>Subscribe</span> <span class="show-for-sr">to the newsletter</span></button></li>
        </ul>
    </nav>
</template>

<script>
import mainMenu from '~/components/header_footer/mainMenu'

export default {
  components: {
      mainMenu
  },
  props: {
    backgroundMenu: String
  },
  methods: {
      openPopin: function () {
          document.getElementById('popin_newsletter').classList.add('opened');
          document.body.classList.add('popin_open');
      },
      openMenu: function () {
          document.getElementById('mainMenu').classList.toggle('menuActive');
          document.body.classList.toggle('popin_open');

          var text = this.$el.querySelector('span:not(.btn)').innerHTML;
          if (text === "Menu") {
                this.$el.querySelector('span:not(.btn)').innerHTML = "Close";
            } else {
                this.$el.querySelector('span:not(.btn)').innerHTML = "Menu";
            }

        this.$el.querySelector('.btn').classList.toggle('toCross');
        
      }
  }
}
</script>