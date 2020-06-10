<template>
    <header role="banner">
        <uiNav/>
        <accessPanel/>
    </header>
</template>

<script>
import uiNav from '~/components/header_footer/uiNav'
import accessPanel from '~/components/header_footer/Access'

export default {
  components: {
      uiNav, accessPanel
  }
}
</script>