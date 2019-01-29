<template>
  <div class="home">

    <img alt="Vue logo" src="../assets/logo.png">

    <span v-if="pageNotFound">
      {{`pageNotFound: ` + pageNotFound}}
    </span>

  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HelloWorld from '@/components/HelloWorld.vue'
var json = require('@/static/content.json')

export default Vue.extend({
  name: 'project',
  components: {
    HelloWorld
  },
  data () {
    return {
      page: {},
      uri: this.$route.params.id,
      pageNotFound: false
    }
  },
  mounted () {
    json[this.uri] === undefined
    ? this.pageNotFound = true
    : this.page = json[this.uri]
    console.log(json)
  }
})
</script>