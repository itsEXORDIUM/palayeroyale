<template>
    <nav>
        <a href="#" class="action">Tickets</a>
        <button id="btn_menu">
            <svg width="26" height="20" viewBox="0 0 26 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M0 8.33333H19.5V11.6667H0V8.33333ZM0 0H26V3.33333H0V0ZM0 20H11.7569V16.6667H0V20Z" fill="#F2F2F2"/>
            </svg>
            <span>Menu</span>
        </button>
        <ul>
            <li><nuxt-link to="/">Home</nuxt-link></li>
            <li><a href="#">Store</a></li>
            <li><nuxt-link to="/tourDates">Tour Dates</nuxt-link></li>
            <li><nuxt-link to="/royalTelevision">Royal Television</nuxt-link></li>
            <li><nuxt-link to="/music">Music</nuxt-link></li>
            <li><nuxt-link to="/about">About</nuxt-link></li>
        </ul>
    </nav>
</template>

<script>
export default {
  components: {
  }
}
</script>

<style lang="scss" scoped>
nav ul {display:none;}
</style>