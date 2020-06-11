<template>
    <div id="news" class="bloc_home">
      <div>
        <h2 v-if="home" class="title_home">Latest News</h2>
        <h1 class="title_home" v-else>{{pageTitle}}</h1>
        <p v-if="home" class="subtitle">See what the bastards are up to.</p>
      </div>
      <div v-if="home">
        <div v-for="(card, index) in news.slice(0, 3)" :key="index" :class="[{ hover_card : index === 1 }, 'news_card']" @mouseover="hoverNews($event)">
          <div class="content">
            <h3 class="title" v-html="card.title.rendered"></h3>
            <div class="subtitle" v-html="card.excerpt.rendered"></div>
            <nuxt-link :to="`/edito/${card.id}`" class="action"><span>Read more</span></nuxt-link>
          </div>
          <img :src="card._embedded['wp:featuredmedia']['0'].source_url" alt=""/>
        </div>
      </div>
      <div v-else>
        <div v-for="(card, index) in news" :key="index" :class="[{ hover_card : index === 1 }, 'news_card']" @mouseover="hoverNews($event)">
          <div class="content">
            <h3 class="title" v-html="card.title.rendered"></h3>
            <div class="subtitle" v-html="card.excerpt.rendered"></div>
            <nuxt-link :to="`/edito/${card.id}`" class="action"><span>Read more</span></nuxt-link>
          </div>
          <img :src="card._embedded['wp:featuredmedia']['0'].source_url" alt=""/>
        </div>
      </div>
      <div v-if="home" class="big_action">
        <nuxt-link to="/palayeroyale/news" class="action"><span>More News</span></nuxt-link>
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
  mounted() {
    document.querySelector('#news>div:first-of-type').classList.add('bloc_title','wrap','fadein','delay');
    document.querySelector('#news>div:nth-of-type(2)').classList.add('container_news','fadein','delay_two');
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