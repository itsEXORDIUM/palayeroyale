<template>
    <div id="news" class="bloc_home wrap">
      <div class="bloc_title">
        <h2 class="title_home">Latest News</h2>
        <p class="subtitle">See what the bastards are up to.</p>
      </div>
      <div class="container_news">
        <div class="news_card" ref="card" v-for="(card, index) in news" :key="index" @mouseover="hoverNews(event)">
          <div class="content">
            <h3 class="title" v-html="card.title.rendered"></h3>
            <div class="subtitle" v-html="card.excerpt.rendered"></div>
            <a :href="card.link" class="action"><span>Read more</span></a>
          </div>
          <img :src="card._embedded['wp:featuredmedia']['0'].source_url" alt=""/>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    news: Array
  },
  created: function() {
    // const vm = this;
    // console.log(this.$refs.card[1]);
  },
  methods: {
    hoverNews: function(event) {
      // document.querySelector('.card_news.hover').classList.remove('hover');
    }
  }
}
</script>