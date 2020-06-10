<template>
    <div>
        <Header/>
        <nuxt/>
        <Footer/>
        <popinNewsletter/>
    </div>
</template>
<script>
const Header = require('~/components/header_footer/header');
const Footer = require('~/components/header_footer/footer');
const popinNewsletter = require('~/components/popins/newsletter');
const axios = require('axios');

export default {
  components: {
    Header, Footer, popinNewsletter
  },
  data() {
    return {
      siteData: []
    }
  },
  mounted() {
    // Get Site Data
    axios.get('http://51.15.241.193/wp-json/')
      .then(response => {
          this.siteData = response.data;
      })

    // Scroll event
    window.onscroll = function() {
        if(document.documentElement.scrollTop > 300 || document.body.scrollTop > 300) {
          document.body.classList.add('backgroundHeader');
        } else if (document.documentElement.scrollTop < 300 || document.body.scrollTop < 300) {
          document.body.classList.remove('backgroundHeader');
        }
    }

    if(window.innerWidth < 640) {
      document.querySelector('body').classList.add('fira');

      var secondaryMenu = this.$el.querySelector('#secondaryMenu');
      var secondaryMenuPhone = this.$el.querySelector('#secondaryMenuPhone');
      secondaryMenu.remove();
      secondaryMenuPhone.prepend(secondaryMenu);
    }
  }
}
</script>
