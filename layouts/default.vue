<template>
    <div>
        <Header/>
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
      siteData: []
    }
  },
  mounted() {
    // Get Site Data
    axios.get('http://51.15.241.193/wp-json/')
      .then(response => {
          this.siteData = response.data;
      })
  }
}
</script>
<style lang="scss">
</style>
