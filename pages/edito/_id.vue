<template>
    <div id="edito" class="news_detail wrap">
      <div class="content">
        <h1 v-html="title"></h1>
        <div class="content_type" v-html="content"></div>
        <nuxt-link class="action" to="/palayeroyale/news"><span>Back to the News</span></nuxt-link>
      </div>
      <img :src="image" alt=""/>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      id : this.$route.params.id,
      news : [],
      title : '',
      content : '',
      image: ''
    }
  },
  mounted() {
    // Get News Posts
    axios.get('https://palayewordpress.planethoster.world/Palaye/wp-json/wp/v2/posts?_embed')
      .then(response => {
        this.news = response.data;
        this.news.forEach(element => {
          if (parseInt(element.id) == this.id) {
            this.title = element.title.rendered;
            this.content = element.content.rendered;
            this.image = element._embedded['wp:featuredmedia']['0'].source_url;
          }
        });
      })
  }
}
</script>