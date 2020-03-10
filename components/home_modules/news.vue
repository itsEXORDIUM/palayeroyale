<template>
    <div id="news" class="bloc_home">
      <div class="bloc_title wrap">
        <h2 v-if="home" class="title_home">Latest News</h2>
        <h1 class="title_home" v-else>{{pageTitle}}</h1>
        <p v-if="home" class="subtitle">See what the bastards are up to.</p>
      </div>
      <div v-if="home" class="container_news">
        <div v-for="(card, index) in news.slice(0, 3)" :key="index" :class="[{ hover_card : index === 1 }, 'news_card']" @mouseover="hoverNews($event)">
          <div class="content">
            <h3 class="title" v-html="card.title.rendered"></h3>
            <div class="subtitle" v-html="card.excerpt.rendered"></div>
            <a :href="card.link" class="action"><span>Read more</span></a>
          </div>
          <img :src="card._embedded['wp:featuredmedia']['0'].source_url" alt=""/>
        </div>
      </div>
      <div class="container_news" v-else>
        <div v-for="(card, index) in news" :key="index" :class="[{ hover_card : index === 1 }, 'news_card']" @mouseover="hoverNews($event)">
          <div class="content">
            <h3 class="title" v-html="card.title.rendered"></h3>
            <div class="subtitle" v-html="card.excerpt.rendered"></div>
            <a :href="card.link" class="action"><span>Read more</span></a>
          </div>
          <img :src="card._embedded['wp:featuredmedia']['0'].source_url" alt=""/>
        </div>
      </div>
      <div v-if="home" class="big_action">
        <nuxt-link to="/news" class="action"><span>More News</span></nuxt-link>
      </div>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    news: Array,
    home: Boolean,
    pageTitle: String
  },
  methods: {
    hoverNews: function(event) {
      var cardHover = this.$el.querySelector('.hover_card');
      cardHover.classList.remove('hover_card');
      event.target.closest('.news_card').classList.add('hover_card');
    }
  }
}
</script>