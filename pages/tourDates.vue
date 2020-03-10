<template>
    <div id="page" class="tourdates">
        <div class="imgs">
            <img :src="featuredImage" alt=""/>
            <img :src="img_one" alt=""/>
            <img :src="img_two" alt=""/>
        </div>
        <tourDates :tourDates="tourDates" :home="home"/>
    </div>
</template>

<script>
import tourDates from '~/components/home_modules/tourDates'
import axios from 'axios'

export default {
    components: {
      tourDates
    },
    data() {
        return {
            tourDates: [],
            home: false,
            featuredImage: '',
            img_one: '',
            img_two: ''
        }
    },
    mounted() {
        // Get Tour Dates Posts
        axios.get('http://51.15.241.193/wp-json/wp/v2/Tour_Dates')
        .then(response => {
            this.tourDates = response.data;
        })

        // Get Page Data
        axios.get('http://51.15.241.193/wp-json/wp/v2/pages/14?_embed')
        .then(response => {
            this.featuredImage = response.data._embedded['wp:featuredmedia']['0'].source_url;
            this.img_one = response.data.acf.picture_1;
            this.img_two = response.data.acf.picture_2;
        })
    }
}
</script>