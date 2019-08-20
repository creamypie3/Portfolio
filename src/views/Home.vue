<template>
  <div class="home">
    <b-container fluid class="p-0 hero">
      <b-row class = "height-50">
        <b-col
          sm = 12
          md = 12
        >
          <img class="background-sky" src = "../../public/img/Splash/splash.png">
          <img class= "back-grass" src = "../../public/img/Splash/splash1.png">
        </b-col>
      </b-row>
    </b-container>
    <b-container fluid class="p-0">
      <b-row class="height-50">
        <b-col
          sm=12
          md=12
        >
          <h2>
            How Might I...
          </h2>
          <p><b>Write a description that is super cool and makes you remember me.</b><br>
            Just kidding! I'm Estelle, a designer and developer who is currently studying Computer Science. 
            I'm currently a UI/UX intern at 
            <a href="https://www.td.com/ca/en/personal-banking/" target="_blank"> TD</a>
            , where I have developed a passion for creating solutions centered around humans and the key principle to always remember 
            <i>who am I building for.</i>
          </p>
        </b-col>
        <b-col
          sm=12
          md=6
        >
          <div
            class="h-100 w-100 d-block background-image"
          >

          </div>
          <!-- <img alt="Vue logo" src="../assets/General/Portrait.jpeg"> -->
          <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
        </b-col>
      </b-row>
      <b-row
        class="height-50"
        no-gutters = true
        v-for="(page, key, index) in json"
        :key="page.id"
      >
        <b-col
          sm=12
          md=6
          :class="{'order-md-2': index % 2 == 0 }"
        >
          <a :href="'/project/' + key">
            <img
              :src="'/img' + page.featuredImage"
              style=background-color: page.color
            />
          </a>
        </b-col>
        <b-col
          sm=12
          md=6
          class="light vertical-align"
          :class="{'order-md-1': index % 2 == 1 }"
        >
          <a :href="'/project/' + key"
          >
            <h3>
              {{page.title}}
            </h3>
            <p>
              {{page.description}}
            </p>
          </a>
        </b-col>
      </b-row>

    </b-container>
  </div>
</template>

<style lang="scss">
  @import "../assets/variables.scss";
img {
  width: 100%;

}
.height-50 {
  min-height: 50vh;
  max-height: 80vh;
  background: white;
  color: black;
  a {
    color: black;
    width: 100%;
    &:hover{
    color: $primary-blue;
    text-decoration: none;
  }
  
  }
}
.background-image {
  background-size: cover;
  background-position: center;
}
.vertical-align{
  display: flex;
  align-items: center;
}
.hero{
  height: 600px;
  .background-sky{
    z-index: 0;
    position: absolute;
    object-fit: cover;
    height: 600px;
  }
  .back-grass{
    z-index: 1;
    position: relative;
    object-fit: cover;
    height: 600px;
  }

}

</style>

<script>
import Vue from 'vue';
import HelloWorld from '@/components/HelloWorld.vue';
import simpleParallax from 'simple-parallax-js';
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
  },
  mounted () {
    var image = document.getElementsByClassName('back-grass');
    var instance = new simpleParallax(image, {
    overflow: true,
    scale: 1.4
    });
  },
  beforeDestroy () {
    instance.destroy();
  }
})
</script>
`
