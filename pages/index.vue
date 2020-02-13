<template>
  <div>
    <div id="cover_img">
      <img :src="featuredImage" alt=""/>
      <div class="bloc_titre_logo wrap">
        <h1>Palaye Royale</h1>
      </div>
    </div>
    <div class="mini_modules wrap">
      <latestVideos :firstVideo="firstVideo" :secondVideo="secondVideo"/>
      <latestSong :songTitle="songTitle" :songCover="songCover"/>
    </div>
    <tourDates :tourPoster="tourPoster"/>
    <news/>
    <newsletter :newsletterImg="newsletterImg"/>
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
      songTitle: '',
      songCover: '',
      firstVideo: [],
      secondVideo: [],
      tourPoster: '',
      newsletterImg: ''
    }
  },
  mounted() {
    // Get Home Page Data
    axios.get('http://51.15.241.193/wp-json/wp/v2/pages/10')
      .then(response => {
          this.homeData = response.data;
          this.featuredId = response.data.featured_media;
          this.getFeaturedImage();

          this.songTitle = response.data.acf.song_title;
          this.songCover = response.data.acf.song_cover;

          this.firstVideo = response.data.acf.first_video;
          this.secondVideo = response.data.acf.second_video;

          this.tourPoster = response.data.acf.tour_poster;
          this.newsletterImg = response.data.acf.newsletter_image;

      })
  },
  methods: {
      getFeaturedImage: function () {
        // Get Featured Image
        axios.get('http://51.15.241.193/wp-json/wp/v2/media/')
          .then(response => {
              this.medias = response.data;
              for(var i = 0; i<this.medias.length; i++) {
                  if (this.medias[i].id == this.featuredId) {
                    this.featuredImage = this.medias[i].source_url;
                  }
              }
          })
      }
  }
}
</script>