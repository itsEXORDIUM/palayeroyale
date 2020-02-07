<template>
    <ul id="mainMenu">
        <li><nuxt-link to="/">Home</nuxt-link></li>
        <li><nuxt-link to="/tourDates">Tour Dates</nuxt-link></li>
        <li><nuxt-link to="/royalTelevision">Royal Television</nuxt-link></li>
        <li><nuxt-link to="/news">News</nuxt-link></li>
        <li><a href="#">Music</a></li>
        <li><nuxt-link to="/about">About</nuxt-link></li>
    </ul>
</template>

<script>
export default {
  components: {
  }
}
</script>

<style scoped>
#mainMenu {display:none;}
</style>