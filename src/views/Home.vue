<template>
  <div class="home">
    <b-container fluid class="p-0">
      <b-row class="height-50">
        <b-col
          sm=12
          md=6
        >
          <h2>
            Welcome to my site
          </h2>
        </b-col>
        <b-col
          sm=12
          md=6
        >
          <div
            :style="{backgroundImage: '/img/Portrait.jpeg'}"
            class="h-100 w-100"
          >

          </div>
          <img alt="Vue logo" src="../assets/General/Portrait.jpeg">
          <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
        </b-col>
      </b-row>
      <b-row
        class="height-50"
        v-for="page in json"
        :key="page.id"
      >
        <b-col
          sm=12
          md=6
        >
          left
          <img
            :src="'/img' + page.featuredImage"
          />
        </b-col>
        <b-col
          sm=12
          md=6
        >
        right
        </b-col>
      </b-row>


    </b-container>
  </div>
</template>

<style lang="scss">
img {
  width: 100%
}
.height-50 {
  min-height: 50vh;
  max-height: 80vh;
}
</style>


<script lang="ts">
import Vue from 'vue'
import HelloWorld from '@/components/HelloWorld.vue'
var json = require('@/static/content.json')
 // @ is an alias to /src

export default Vue.extend({
  name: 'home',
  components: {
    HelloWorld
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
`