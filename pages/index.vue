<template>
  <div id="page" class="home">
    <div id="cover_img">
      <img :src="featuredImage" alt=""/>
      <div class="bloc_titre_logo">
        <h1>Palaye Royale</h1>
      </div>
    </div>
    <div class="mini_modules wrap">
      <latestVideos :firstVideo="firstVideo" :secondVideo="secondVideo"/>
      <latestSong :songTitle="songTitle" :songCover="songCover" :deezer="deezer" :spotify="spotify" :youtube_music="youtube_music" :google_play="google_play" :amazon_music="amazon_music" :itunes="itunes"/>
    </div>
    <tourDates :tourPoster="tourPoster" :tourDates="tourDates" :home="home"/>
    <news :news="news" :home="home"/>
    <newsletter :newsletterImg="newsletterImg" :popin="popin"/>
  </div>
</template>

<script>
import latestVideos from '~/components/home_modules/latestVideos'
import latestSong from '~/components/home_modules/latestSong'
import tourDates from '~/components/home_modules/tourDates'
import news from '~/components/home_modules/news'
import newsletter from '~/components/home_modules/newsletter'
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
      featuredImage: '',
      medias: [],
      songTitle: '',
      songCover: '',
      deezer: '',
      youtube_music: '',
      spotify: '',
      google_play: '',
      amazon_music: '',
      itunes: '',
      firstVideo: [],
      secondVideo: [],
      tourPoster: '',
      tourDates: [],
      newsletterImg: '',
      popin: false,
      news: [],
      home: true
    }
  },
  mounted() {
    // Get Home Page Data
    axios.get('http://51.15.241.193/wp-json/wp/v2/pages/10?_embed')
      .then(response => {
          this.homeData = response.data;
          this.featuredImage = response.data._embedded['wp:featuredmedia']['0'].source_url;

          this.songTitle = response.data.acf.song_title;
          this.songCover = response.data.acf.song_cover;
          this.deezer = response.data.acf.deezer;
          this.youtube_music = response.data.acf.youtube_music;
          this.spotify = response.data.acf.spotify;
          this.google_play = response.data.acf.google_play;
          this.amazon_music = response.data.acf.amazon_music;
          this.itunes = response.data.acf.itunes;

          this.firstVideo = response.data.acf.first_video;
          this.secondVideo = response.data.acf.second_video;

          this.tourPoster = response.data.acf.tour_poster;
          this.newsletterImg = response.data.acf.newsletter_image;

      })

    // Get Tour Dates Posts
    axios.get('http://51.15.241.193/wp-json/wp/v2/Tour_Dates')
      .then(response => {
        this.tourDates = response.data;
      })

    // Get News Posts
    axios.get('http://51.15.241.193/wp-json/wp/v2/posts?_embed')
      .then(response => {
        this.news = response.data;
      })

    document.getElementById('cover_img').classList.add('opentobottom','light_delay');
    document.getElementById('latest_videos').classList.add('fadein','delay_one');
    document.getElementById('latest_song').classList.add('fadein','delay_two');
  }
}
</script>