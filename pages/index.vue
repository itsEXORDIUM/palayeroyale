<template>
  <div>
    <div id="cover_img">
      <img :src="featuredImage" alt=""/>
      <div class="bloc_titre_logo wrap">
        <h1>Palaye Royale</h1>
      </div>
    </div>
    <latestVideos/>
    <latestSong/>
    <tourDates/>
    <news/>
    <newsletter/>
  </div>
</template>

<script>
import latestVideos from '~/components/home_modules/latestVideos'
import latestSong from '~/components/home_modules/latestSong'
import tourDates from '~/components/post_types/tourDates'
import news from '~/components/post_types/news'
import newsletter from '~/components/popins/newsletter'
import axios from 'axios'

export default {

  head () {
    return {
      title: 'Palaye Royale | Official Website',
      meta: [
        { hid: 'description', name: 'description', content: 'The official website of the band Palaye Royale'}
      ]
    }
  },
  components: {
      latestVideos, latestSong, tourDates, news, newsletter
  },
  data() {
    return {
      homeData: [],
      featuredId: '',
      featuredImage: '',
      medias: [],
      itemTest: []
    }
  },
  mounted() {
    // Get Home Page Data
    axios.get('http://51.15.241.193/wp-json/wp/v2/pages/10')
      .then(response => {
          this.homeData = response.data;
          this.featuredId = response.data.featured_media;
      })

    // Get Featured Image
    axios.get('http://51.15.241.193/wp-json/wp/v2/media/')
      .then(response => {
          this.medias = response.data;
          var position = 0;
          this.medias.forEach(function (item) {
              if (item.id === this.featuredId) {
                this.itemTest = item;
                this.featuredImage = item.source_url;
              }
              position++;
          }.bind(this));
      })
  }
}
</script>