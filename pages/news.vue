<template>
    <div id="page" class="newsPage" role="main">
        <news :news="news" :home="home" :pageTitle="pageTitle"/>
    </div>
</template>

<script>
import news from '~/components/home_modules/news'
import axios from 'axios'

export default {
    name: 'News',
    data() {
        return {
          pageData: [],
          pageTitle: '',
          home: false,
          news: []
        }
    },
    components: {
      news
    },
    mounted() {
        // Get Page Data
        axios.get('http://51.15.241.193/wp-json/wp/v2/pages/8?_embed')
        .then(response => {
            this.pageData = response.data;
            this.pageTitle = response.data.title.rendered;
        })

        // Get News Posts
        axios.get('http://51.15.241.193/wp-json/wp/v2/posts?_embed')
        .then(response => {
            this.news = response.data;
        })
    }
}
</script>