<template>
  <div class="main-navbar">
    <router-link to="/parameters" class="main-navbar__item">Параметры</router-link>
    <router-link to="/questions" class="main-navbar__item">Вопросы</router-link>
    <router-link to="/logic" class="main-navbar__item">Логика</router-link>
    <router-link to="/conditions" class="main-navbar__item">Условия</router-link>
    <router-link to="/respondents" class="main-navbar__item">Респонденты</router-link>
  </div>
</template>

<script>
export default {
  name: 'MainNavbar'
}
</script>

<style lang="scss">
.main-navbar {
  width: 100%;
  margin: 20px auto 0 auto;
  padding: 15px 0 0 0;
  text-align: left;
  &__item {
    display: inline-block;
    color: #318C44;
    text-decoration: none;
    padding: 10px 20px;
    margin-right: 20px;
    &:hover {
      color: #318C44;
      text-decoration: none;
    }
  }
  .nuxt-link-active {
    color: #000;
    border-bottom: 3px solid #C1E837;
  }
}
</style>
