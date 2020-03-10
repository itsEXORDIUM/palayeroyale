<template>
    <div id="page" class="royaltv">
      <div id="royaltv" class="bloc_home wrap">
        <div class="bloc_title">
          <h1 class="title_home">{{pageTitle}}</h1>
          <p class="subtitle">Watch the tour vlogs.</p>
        </div>
        <div class="cinema">
          <div class="episodes">
          </div>
          <div class="tv_links">
            <div class="tv">
              <img src="~assets/img/tv.png" alt=""/>
            </div>
            <div class="big_action">
              <a href="#" class="action"><span>Watch on Youtube</span></a>
              <button class="action"><span>Fullscreen</span></button>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
          pageData: [],
          pageTitle: ''
        }
    },
    mounted() {
        // Get Page Data
        axios.get('http://51.15.241.193/wp-json/wp/v2/pages/12?_embed')
        .then(response => {
            this.pageData = response.data;
            this.pageTitle = response.data.title.rendered;
        })
    }
}
</script>