<template>
  <div id="app">
    <Header/>
    <!-- Dynamic Content -->
    <router-view />

   <Footer/>
  </div>

</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Lato&display=swap');
#app {
  font-family: 'Lato', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  font-size: 16px !important;
}

</style>

<script lang="ts">
import Vue from 'vue'
import Header from './Header.vue'
import Footer from './Footer.vue'
import Next from './Next.vue'
var json = require('@/static/content.json')
// @ is an alias to /src

export default Vue.extend({
  name: 'home',
  components: {
    Header,
    Footer,
    Next
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
