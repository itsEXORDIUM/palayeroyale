<template>
    <div id="page" class="aboutPage">
      <div class="bloc_home">
        <div class="bloc_title wrap">
          <h1 class="title_home">{{pageTitle}}</h1>
        </div>
        <div class="bandmembers wrap">
          <div class="bandmember remi" @mouseover="mbImg($event)" @mouseout="mbImgBack()">
            <p class="name">{{mbone.name}}</p>
            <div class="line">
              <p class="nickname">{{mbone.nickname}}</p>
              <ul class="socials">
                <li v-if="mboneSocials.twitter" class="twitter"><a :href="mboneSocials.twitter" title="Follow the band on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                <li v-if="mboneSocials.instagram" class="instagram"><a :href="mboneSocials.instagram" title="Follow the band on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                <li v-if="mboneSocials.facebook" class="facebook"><a :href="mboneSocials.facebook" title="Follow the band on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
              </ul>
            </div>
            <p class="role">{{mbone.role}}</p>
          </div>
          <div class="bandmember seb" @mouseover="mbImg($event)" @mouseout="mbImgBack()">
            <p class="name">{{mbtwo.name}}</p>
            <div class="line">
              <p class="nickname">{{mbtwo.nickname}}</p>
              <ul class="socials">
                <li v-if="mbtwoSocials.twitter" class="twitter"><a :href="mbtwoSocials.twitter" title="Follow the band on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                <li v-if="mbtwoSocials.instagram" class="instagram"><a :href="mbtwoSocials.instagram" title="Follow the band on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                <li v-if="mbtwoSocials.facebook" class="facebook"><a :href="mbtwoSocials.facebook" title="Follow the band on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
              </ul>
            </div>
            <p class="role">{{mbtwo.role}}</p>
          </div>
          <div class="bandmember em" @mouseover="mbImg($event)" @mouseout="mbImgBack()">
            <p class="name">{{mbthree.name}}</p>
            <div class="line">
              <p class="nickname">{{mbthree.nickname}}</p>
              <ul class="socials">
                <li v-if="mbthreeSocials.twitter" class="twitter"><a :href="mbthreeSocials.twitter" title="Follow the band on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                <li v-if="mbthreeSocials.instagram" class="instagram"><a :href="mbthreeSocials.instagram" title="Follow the band on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                <li v-if="mbthreeSocials.facebook" class="facebook"><a :href="mbthreeSocials.facebook" title="Follow the band on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
              </ul>
            </div>
            <p class="role">{{mbthree.role}}</p>
          </div>
        </div>
        <div class="img bandMb">
          <img :src="featuredImage" alt=""/>
        </div>
      </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  head () {
    return {
      title: 'About — Palaye Royale',
      meta: [
        { hid: 'description', name: 'description', content: 'Everything about Palaye Royale'}
      ]
    }
  },
  data() {
        return {
          pageData: [],
          pageTitle: '',
          featuredImage: '',
          mbone: [],
          mboneSocials: [],
          mbtwo: [],
          mbtwoSocials: [],
          mbthree: [],
          mbthreeSocials: []
        }
    },
  mounted() {
        // Get Page Data
        axios.get('http://51.15.241.193/wp-json/wp/v2/pages/6?_embed')
        .then(response => {
            this.pageData = response.data;
            this.pageTitle = response.data.title.rendered;
            this.featuredImage = response.data._embedded['wp:featuredmedia']['0'].source_url;
            this.mbone = response.data.acf.band_member;
            this.mboneSocials = response.data.acf.band_member.socialmedias;
            this.mbtwo = response.data.acf.band_member_2;
            this.mbtwoSocials = response.data.acf.band_member_2.socialmedias;
            this.mbthree = response.data.acf.band_member_3;
            this.mbthreeSocials = response.data.acf.band_member_3.socialmedias;
        })

      document.querySelector('.title_home').classList.add('fadein','delay_one');
      document.querySelector('.img').classList.add('opentobottom','delay');
      document.querySelector('.bandmembers').classList.add('fadein','delay_two');
  },
  methods: {
      mbImg: function (event) {
        document.querySelector('.img').classList.remove('opentobottom','delay');

        var bandMb = event.target.closest('.bandmember');
        if (bandMb.classList.contains('remi')) {
          this.$el.querySelector('.bandMb img').src = this.mbone.picture;
        } else if (bandMb.classList.contains('seb')) {
          this.$el.querySelector('.bandMb img').src = this.mbtwo.picture;
        } else if (bandMb.classList.contains('em')) {
          this.$el.querySelector('.bandMb img').src = this.mbthree.picture;
        }

        document.querySelector('.img').classList.add('opentobottom');
      },
      mbImgBack: function () {
        this.$el.querySelector('.bandMb img').src = this.featuredImage;
      }
  }
}
</script>