<template>
  <div class="home">

    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->

    <span v-if="pageNotFound">
      {{`pageNotFound: ` + pageNotFound}}
    </span>
    <!-- page content -->
    <b-conatiner v-if="pageNotFound !== true">
      <b-row
        class="mt-5 mb-5"
      >
        <b-col
          class="mt-5 mb-5"
        >
          <h1>
            {{page.title}}
          </h1>
          <h4>
            {{page.description}}
          </h4>
        </b-col>
      </b-row>
      <b-row
        v-for="(block, index) in page.html"
        :key="index"
      >
        <b-col
          class="project-block"
          v-if="block.type === 'text'"
          md="8"
          offset-md="2"
        >
          <p>{{block.text}}</p>
        </b-col>
        <b-col
          class="project-block"
          v-if="block.type === 'image'"
          md="8"
          offset-md="2"
        >
          <div
            class="image-wrapper"
            v-for="image in block.images"
            v-bind:key="image.url"
          >
            <img :alt="image.title" :src="'/img' + image.url">
            <p v-if="image.title.length>0"
              class = "image-caption"
              >
                {{image.title}}
            </p>
          </div>
        </b-col>
      </b-row>
    </b-conatiner>
    <Next/>
  </div>

</template>

<style lang="scss">
.project-block {
  margin-bottom: 25px;
  padding: 15px;
  font-size: 16px;
  text-align: justify;
  img {
    margin-bottom: 25px;
  }
  .image-caption {
  font-size: 12px;
  text-align: left;
  margin-top:-25px;
  padding: 15px;
  }
  video {
    margin-bottom: 25px;
  }
  .video-caption {
    font-size: 12px;
    text-align: left;
    margin-top:-25px;
    padding: 15px;
   }
}

</style>

<script lang="ts">
import Vue from 'vue'
import HelloWorld from '@/components/HelloWorld.vue'
import Next from '../Next.vue'
var json = require('@/static/content.json')

export default Vue.extend({
  name: 'project',
  components: {
    HelloWorld,
    Next
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
