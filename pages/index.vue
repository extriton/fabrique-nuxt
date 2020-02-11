<template>
  <section class="page-container">
    <main-navbar/>
    <nuxt-child></nuxt-child>
  </section>
</template>

<script>
import MainNavbar from '~/components/MainNavbar.vue'

export default {
  components: {
    MainNavbar
  }
}
</script>

<style lang="SCSS">
.page-container {
  width: 60%;
  margin: 0 auto;
}
</style>
