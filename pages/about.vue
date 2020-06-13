<template>
    <div id="page" class="aboutPage" role="main">
      <div class="bloc_home">
        <div class="bloc_title wrap">
          <h1>{{pageTitle}}</h1>
        </div>
        <div>
          <div class="bandmember remi" @mouseover="mbImg($event)" @mouseout="mbImgBack()">
            <div class="imgmb"><img :src="mbone.picture" class="hide-for-big" alt=""/></div>
            <p class="name">{{mbone.name}}</p>
            <div class="line">
              <p class="nickname">{{mbone.nickname}}</p>
              <ul class="socials">
                <li v-if="mboneSocials.twitter" class="twitter"><a :href="mboneSocials.twitter" title="Follow Remington on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                <li v-if="mboneSocials.instagram" class="instagram"><a :href="mboneSocials.instagram" title="Follow Remington on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                <li v-if="mboneSocials.facebook" class="facebook"><a :href="mboneSocials.facebook" title="Follow Remington on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
              </ul>
            </div>
            <p class="role">{{mbone.role}}</p>
          </div>
          <div class="bandmember seb" @mouseover="mbImg($event)" @mouseout="mbImgBack()">
            <div class="imgmb"><img :src="mbtwo.picture" class="hide-for-big" alt=""/></div>
            <p class="name">{{mbtwo.name}}</p>
            <div class="line">
              <p class="nickname">{{mbtwo.nickname}}</p>
              <ul class="socials">
                <li v-if="mbtwoSocials.twitter" class="twitter"><a :href="mbtwoSocials.twitter" title="Follow Sebastian on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                <li v-if="mbtwoSocials.instagram" class="instagram"><a :href="mbtwoSocials.instagram" title="Follow Sebastian on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                <li v-if="mbtwoSocials.facebook" class="facebook"><a :href="mbtwoSocials.facebook" title="Follow Sebastian on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
              </ul>
            </div>
            <p class="role">{{mbtwo.role}}</p>
          </div>
          <div class="bandmember em" @mouseover="mbImg($event)" @mouseout="mbImgBack()">
            <div class="imgmb"><img :src="mbthree.picture" class="hide-for-big" alt=""/></div>
            <p class="name">{{mbthree.name}}</p>
            <div class="line">
              <p class="nickname">{{mbthree.nickname}}</p>
              <ul class="socials">
                <li v-if="mbthreeSocials.twitter" class="twitter"><a :href="mbthreeSocials.twitter" title="Follow Emerson on Twitter (New Window)" target="_blank"><span class="show-for-sr">Twitter</span></a></li>
                <li v-if="mbthreeSocials.instagram" class="instagram"><a :href="mbthreeSocials.instagram" title="Follow Emerson on Instagram (New Window)" target="_blank"><span class="show-for-sr">Instagram</span></a></li>
                <li v-if="mbthreeSocials.facebook" class="facebook"><a :href="mbthreeSocials.facebook" title="Follow Emerson on Facebook (New Window)" target="_blank"><span class="show-for-sr">Facebook</span></a></li>
              </ul>
            </div>
            <p class="role">{{mbthree.role}}</p>
          </div>
        </div>
        <div>
          <img :src="featuredImage" alt=""/>
        </div>
      </div>
      <div class="imgs">
          <div class="img_container">
            <img :src="pictureone" alt=""/>
          </div>
          <div class="img_container">
            <img :src="picturetwo" alt=""/>
          </div>
      </div>
      <div class="aboutText wrap" v-html="aboutText"></div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'About',
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
          mbthreeSocials: [],
          pictureone: '',
          picturetwo: '',
          picturethree: '',
          aboutText: {}
        }
    },
  mounted() {
        // Get Page Data
        axios.get('https://palayewordpress.planethoster.world/Palaye/wp-json/wp/v2/pages/6?_embed')
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
            this.pictureone = response.data.acf.picture_one;
            this.picturetwo = response.data.acf.picture_two;
            this.picturethree = response.data.acf.picture_three;
            this.aboutText = response.data.content.rendered;
        })

      document.querySelector('.bloc_title h1').classList.add('title_home','fadein','delay_one');
      document.querySelector('.bloc_home>div:last-of-type').classList.add('hide-for-tab','img','bandMb','opentobottom','delay');
      this.goodbyeAnim();
      document.querySelector('.bloc_home>div:nth-of-type(2)').classList.add('bandmembers','wrap','fadein','delay_two');
  },
  methods: {
      mbImg: function (event) {
        document.querySelector('.img').style.height = 'auto';

        var bandMb = event.target.closest('.bandmember');
        if (bandMb.classList.contains('remi')) {
          this.$el.querySelector('.bandMb img').src = this.mbone.picture;
        } else if (bandMb.classList.contains('seb')) {
          this.$el.querySelector('.bandMb img').src = this.mbtwo.picture;
        } else if (bandMb.classList.contains('em')) {
          this.$el.querySelector('.bandMb img').src = this.mbthree.picture;
        }

        document.querySelector('.img').classList.add('opentobottom');
        this.goodbyeAnim();
      },
      mbImgBack: function () {
        document.querySelector('.img').style.height = 'auto';

        this.$el.querySelector('.bandMb img').src = this.featuredImage;

        document.querySelector('.img').classList.add('opentobottom');
        this.goodbyeAnim();
      },
      goodbyeAnim: function() {
        setTimeout( function(){ 
        document.querySelector('.img').classList.remove('opentobottom','delay'); 
        document.querySelector('.img').style.height = '110vh';
        }, 3000);
      }
  }
}
</script>