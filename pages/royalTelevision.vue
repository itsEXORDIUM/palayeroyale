<template>
    <main role="main" id="page" class="royaltv">
      <div id="royaltv" class="bloc_home wrap">
        <div class="bloc_title">
          <h1 class="title_home">{{pageTitle}}</h1>
          <p class="subtitle">Watch the tour vlogs.</p>
        </div>
        <div class="cinema">
          <div class="episodes">
            <div class="the_seasons">
              <div v-for="(season, index) in seasons" :key="index" :class="[{ opened : index === 'season_one' }, 'a_season']">
                <h2 class="season_title"><button @click="toggleOpen($event)">{{season.title}}</button></h2>
                <ul>
                  <li v-for="(episode, index) in season" :key="index" class="episode">
                    <h3 v-if="episode.slug"><button :data-link="episode.slug" @click="changeEpisode($event)"><span class="action"><span>Watch</span></span> {{episode.title}}</button></h3>
                    <h3 v-if="episode.slug === ''" class="unavailable">Unavailable Episode</h3>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="tv_links">
            <div class="tv">
              <img src="~assets/img/tv.png" alt=""/>
              <iframe width="67%" height="90%" :src="`https://www.youtube.com/embed/${slug}`" frameborder="0" allowfullscreen></iframe>
            </div>
            <div class="big_action">
              <a :href="'https://www.youtube.com/watch?v=' + slug" class="action" target="_blank" title="Watch the episode on Youtube (New Window)"><span>Watch on Youtube</span></a>
            </div>
          </div>
        </div>
      </div>
    </main>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
          pageData: {},
          pageTitle: '',
          slug: '',
          seasons: {}
        }
    },
    mounted() {
        // Get Page Data
        axios.get('http://51.15.241.193/wp-json/wp/v2/pages/12?_embed')
        .then(response => {
            this.pageData = response.data;
            this.pageTitle = response.data.title.rendered;
            this.seasons = response.data.acf;
            this.slug = this.seasons.season_one.episode_1.slug;
        })

        document.querySelector('.bloc_title').classList.add('fadein','delay');
        document.querySelector('.episodes').classList.add('fadein','delay_one');
        document.querySelector('.tv_links').classList.add('fadein','delay_two');
    },
    methods: {
      toggleOpen: function(event) {
        var season = event.target.closest('.a_season');
        if(season.classList.contains('opened')) {
          season.classList.remove('opened');
        } else {
          season.classList.add('opened');
        }
      },

      changeEpisode: function(event) {
        var element = event.target;
        if(element.tagName == 'BUTTON') {
          this.slug = element.dataset.link;
        } else {
          this.slug = element.closest('button').dataset.link;
        }
        
      }
    }
}
</script>