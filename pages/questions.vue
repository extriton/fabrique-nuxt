<template>
  <section class="page-container">
    <main-navbar/>
    <div class="page-container__body">
      <h1>Questions</h1>
    </div>
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

<style lang="scss">
.page-container {
  width: 60%;
  margin: 0 auto;
  &__body {
    border-top: 1px solid #E3F5A4;
  }
}
</style>
