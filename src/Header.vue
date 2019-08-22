<template>
    <b-navbar toggleable="md" type="dark" variant="white" class="d-fixed">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

      <b-navbar-brand href="/">
        <img src="./assets/logo.png"
        class= "logo-img"
        >
      </b-navbar-brand>

      <b-collapse is-nav id="nav_collapse">

        <!-- Right aligned nav items, collapsed on mobile -->
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown text="Projects" right>
            <b-dropdown-item
              v-for="(page, key) in json"
              :key="key"
              :href="'/project/' + key">
              {{page.title}}
            </b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item href="/about" right>About</b-nav-item>
        </b-navbar-nav>

      </b-collapse>
    </b-navbar>

</template>

<style lang="scss">
@import './assets/variables.scss';
  .bg-white{
    background-color: white !important;
    position: fixed !important;
    top: 0px !important;
    z-index: 10 !important;
    width: 100%;
  }
    .d-fixed{
      background-color: white;
    }
    .navbar-dark .navbar-nav .nav-link{
      color: black !important;
    }
    .logo-img{
      width: 100px;
      padding: 15px;
      @media screen and (max-width: 789px){
        width: 60px;
      }
    }
</style>

<script>
var json = require('@/static/content.json')
export default {
  name: 'Header'
}
</script>
