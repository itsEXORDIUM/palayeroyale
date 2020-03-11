<template>
    <div id="popin_newsletter">
        <button v-if="popin" id="close_popin" @click="closePopin()"><span class="show-for-sr">Close the popin</span></button>
        <newsletter :popin="popin"/>
    </div>
</template>

<script>
import newsletter from '~/components/home_modules/newsletter'

export default {
  components: {
    newsletter
  },
  data() {
    return {
      popin: true
    }
  },
  methods: {
      closePopin: function () {
          document.getElementById('popin_newsletter').classList.add('fadeout');
          document.getElementById('popin_newsletter').classList.remove('opened','fadein');
          document.body.classList.remove('popin_open_small');
      }
  }
}
</script>