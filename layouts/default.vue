<template>
    <div>
        <Header :backgroundMenu="backgroundMenu"/>
        <nuxt/>
        <Footer/>
        <popinNewsletter/>
    </div>
</template>
<script>
import Header from '~/components/header_footer/header'
import Footer from '~/components/header_footer/footer'
import popinNewsletter from '~/components/popins/newsletter'
import axios from 'axios'

export default {
  components: {
    Header, Footer, popinNewsletter
  },
  data() {
    return {
      siteData: [],
      backgroundMenu: ''
    }
  },
  mounted() {
    // Get Site Data
    axios.get('http://51.15.241.193/wp-json/')
      .then(response => {
          this.siteData = response.data;
          this.activePage();
      })

    // Scroll event
    window.onscroll = function() {
        if(document.documentElement.scrollTop > 300 || document.body.scrollTop > 300) {
          document.body.classList.add('backgroundHeader');
        } else if (document.documentElement.scrollTop < 300 || document.body.scrollTop < 300) {
          document.body.classList.remove('backgroundHeader');
        }
    }
  },
  methods: {
    activePage : function () {
      var activePage = document.getElementById('page').className;
      this.backgroundMenu = activePage;
    }
  }
}
</script>
