<template>
    <nav class="wrap">
        <button id="btn_menu">
            <svg width="26" height="20" viewBox="0 0 26 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 8.33333H19.5V11.6667H0V8.33333ZM0 0H26V3.33333H0V0ZM0 20H11.7569V16.6667H0V20Z" fill="#f2f2f2"/>
            </svg>
            <span>Menu</span>
        </button>
        <mainMenu/>

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
  methods: {
      openPopin: function () {
          document.getElementById('popin_newsletter').classList.add('opened');
          document.body.classList.add('popin_open');
      }
  }
}
</script>