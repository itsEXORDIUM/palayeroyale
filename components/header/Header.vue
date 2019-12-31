<template>
    <header>
        <LeftColumn/>
        <h1>
            <img src="~/assets/img/LOGO.png" width="229" height="47" alt="Palaye Royale, Official Website"/>
        </h1>
        <uiNav/>
    </header>
</template>

<script>
import uiNav from '~/components/header/uinav'
import LeftColumn from '~/components/header/leftcolumn'

export default {
  components: {
      uiNav, LeftColumn
  }
}
</script>

<style lang="scss">
</style>