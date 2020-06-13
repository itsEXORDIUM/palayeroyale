<template>
    <div>
        <Header/>
        <nuxt/>
        <Footer/>
        <popinNewsletter/>
    </div>
</template>
<script>
import Header from '~/components/header_footer/Header'
import Footer from '~/components/header_footer/Footer'
import popinNewsletter from '~/components/popins/newsletter'
import axios from 'axios'

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
    axios.get('https://palayewordpress.planethoster.world/Palaye/wp-json/wp/v2/')
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
