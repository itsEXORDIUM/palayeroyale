<template>
    <div id="newsletter" class="bloc_home wrap">
      <div class="container_newsletter">
        <div class="bloc_title">
          <h2 class="title_home">Newsletter</h2>
          <p class="subtitle">Sign up with your email address to receive news and updates.</p>
        </div>
        <form>
          <fieldset>
            <legend class="show-for-sr">Newsletter</legend>
            <div class="contain_form">
              <div class="contain_input">
                <label for="signup" class="show-for-sr">Your Email Address</label>
                <input type="text" id="signup" placeholder="Your Email Address"/>
                <p>We respect your privacy.</p>
              </div>
              <div class="big_action">
                <input type="submit" class="action" value="Sign Up"/>
              </div>
            </div>
          </fieldset>
        </form>
      </div>
      <img :src="newsletterImg" alt=""/>
    </div>
</template>

<script>
export default {
  components: {
  },
  props: {
    newsletterImg: String
  }
}
</script>