<template>
  <div id="app">
    <Header/>
    <!-- Dynamic Content -->
    <router-view />

   <Footer/>
  </div>
 
</template>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

<script lang="ts">
import Vue from 'vue'
import Header from './Header.vue'
import Footer from './Footer.vue'
var json = require('@/static/content.json')
// @ is an alias to /src

export default Vue.extend({
  name: 'home',
  components: {
    Header,
    Footer
  },
  data () {
    return {
      json: {}
    }
  },
  mounted () {
    this.json = json
    console.log(json)
  }
})
</script>
