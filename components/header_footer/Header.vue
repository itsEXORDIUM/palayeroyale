<template>
    <header>
        <uiNav :backgroundMenu="backgroundMenu"/>
        <accessPanel/>
    </header>
</template>

<script>
import uiNav from '~/components/header_footer/uinav'
import accessPanel from '~/components/header_footer/Access'

export default {
  components: {
      uiNav, accessPanel
  },
  props: {
    backgroundMenu: String
  }
}
</script>