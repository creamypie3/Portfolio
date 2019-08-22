<template>
  <div class="home">
    <div class="logger" :class="{'active-scroll': isUserScrolling}">{{logger}}</div>
    <section>
      <b-container fluid class="p-0 splash">
        <b-row class="hero">
          <b-col sm="12" md="12" cols="12">
            <figure class="background">
              <img class="background-sky" src="/img/Splash/splash.png" />
            </figure>
            <figure class="foreground">
              <img class="character" src="/img/Splash/splash3.png" />
            </figure>
            <article>
              <img class="back-grass" src="/img/Splash/splash1.png" />
              <img class="front-grass" src="/img/Splash/splash2.png" />
              <img class="lamp-post" src="/img/Splash/splash5.png" />
              <img class="green-table" src="/img/Splash/splash4.png" />
              <img class="wall" src="/img/Splash/room.png" />
              <img class="polaroid" src="/img/Splash/polaroid.png" />
              <img class="desk" src="/img/Splash/desk.png" />
            </article>
          </b-col>
        </b-row>
      </b-container>
    </section>
    <section>
      <b-container fluid class="p-0">
          <b-row class="height-50">
           <b-col sm="12" md="12">
          <h2>How Might I...</h2>
          <p>
            <b>Write a description that is super cool and makes you remember me.</b>
            <br />Just kidding! I'm Estelle, a designer and developer who is currently studying Computer Science.
            I'm currently a UI/UX intern at
            <a
              href="https://www.td.com/ca/en/personal-banking/"
              target="_blank"
            >TD</a>
            , where I have developed a passion for creating solutions centered around humans and the key principle to always remember
            <i>who am I building for.</i>
          </p>
        </b-col>
        <b-col sm="12" md="6">
          <div class="h-100 w-100 d-block background-image"></div>
          <!-- <img alt="Vue logo" src="../assets/General/Portrait.jpeg"> -->
          <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
        </b-col>
        </b-row>
      </b-container>
      <b-container fluid class = "p-5 gallery">
      <b-row class="height-50" no-gutters="true" v-for="(page, key, index) in json" :key="page.id">
        <b-col sm="12" md="6" :class="{'order-md-2': index % 2 == 0 }">
          <a :href="'/project/' + key">
            <img :src="'/img' + page.featuredImage" style="background-color:" page.color class="background-image"/>
          </a>
        </b-col>
        <b-col sm="12" md="6" class="light vertical-align" :class="{'order-md-1': index % 2 == 1 }">
          <a :href="'/project/' + key">
            <h3>{{page.title}}</h3>
            <p>{{page.description}}</p>
          </a>
        </b-col>
      </b-row>
    </b-container>
    </section>
  </div>
</template>

<style lang="scss">
@import "../assets/variables.scss";
body{
  font-size:18px;
}
img {
  width: 100%;
  border-radius: 10px;
  object-fit: cover;
  @media screen and (max-width: $phone){
    padding: 30px;
  }
}
.splash {
  top: -700px;
}
.height-50 {
  display: block;
  min-height: 50vh;
  max-height: 80vh;
  background: white;
  color: black;
  margin: auto;
  a {
    color: black;
    width: 100%;
    &:hover {
      color: $primary-blue;
      text-decoration: none;
    }
  }
  h2 {
    margin-top: 200px;
    font-size: 24px;
  }
  h3 {
    font-size: 24px;
  }
  p {
    width: 50%;
    margin: auto;
    font-size: 18px;
  }
}
.background-image {
  background-size: cover;
  background-position: center;
}
.vertical-align {
  display: flex;
  align-items: center;
}
.logger {
  position: fixed;
  top: 0;
  left: 0;
  background: orange;
  z-index: 9999999;
  &.active-scroll {
    background: yellowgreen;
  }
}
.hero {
  top:-800px;
  //overflow: hidden;
  @media screen and (max-width: $phone){
    display: none;
  }
  .back-grass {
    position: absolute;
    z-index: 1;
    top: 100vh+ $shift-up;
  }
  .front-grass {
    position: absolute;
    z-index: 2;
    top: 110vh+ $shift-up;
  }
  .lamp-post {
    position: absolute;
    bottom: 160vh+ $shift-up;
    z-index: 3;
  }
  .green-table {
    position: absolute;
    z-index: 4;
    top: 140vh+ $shift-up;
  }
  .wall {
    position: absolute;
    z-index: 1;
    top: 200vh+ $shift-up;
  }
  .desk {
    position: absolute;
    z-index: 4;
    top: 200vh+ $shift-up;
    left: 0vh;
  }
  .polaroid {
    position: relative;
    z-index: 4;
    top: 5vh+ $shift-up;
  }
  .foreground {
    z-index: 3;
    width: 100%;
    top:+ $shift-up;
  }
  figure {
    align-items: center;
    height: 100vh;
    margin: 0;
    width: 100%;
    justify-content: center;
    top: $top-offset;
    .background {
      z-index: -1;
    }
    img {
      left: 0px;
      object-fit: cover;
      position: absolute;
      width: 100%;
      height: 100%;
    }
    @media screen and (min-width: $bp) {
      position: sticky;
    }
  }
}

article {
  margin: 0 auto;
  z-index: 1;
}
section {
  margin: 0;
  padding: 0;
  &:not(:last-of-type) {
    margin-bottom: $spacing;
  }
}
</style>

<script>
import Vue from 'vue'
// import HelloWorld from "@/components/HelloWorld.vue";
import simpleParallax from 'simple-parallax-js'
import debounce from 'lodash/debounce'
var json = require('@/static/content.json')
// @ is an alias to /src
const SimpleParallax = simpleParallax

export default Vue.extend({
  name: 'home',
  components: {},
  data () {
    return {
      json: {},
      logger: '',
      isUserScrolling: false
      // shouldFreeze
    }
  },
  methods: {
    handleScroll (event) {
      // Any code to be executed when the window is scrolled
      this.isUserScrolling = window.scrollY > 0
      this.logger = `${window.scrollY} | ${this.isUserScrolling}`
      this.freezeScroll()
    },
    freezeScroll () {
      console.log(window.scrollY)
      if (window.scrollTop > 1200 && window.scrollTop < 1300) {
        console.log('hello')
        disableScroll()
        setTimeout(enableScroll, 2000)
      }
    }
  },

  created () {
    this.handleDebouncedScroll = debounce(this.handleScroll, 80)
    window.addEventListener('scroll', this.handleDebouncedScroll)
    // shouldFreeze = setInterval(freezeScroll,10);
  },

  beforeDestroy () {
    // I switched the example from `destroyed` to `beforeDestroy`
    // to exercise your mind a bit. This lifecycle method works too.
    window.removeEventListener('scroll', this.handleDebouncedScroll)
  },
  mounted () {
    this.json = json
    console.log(json)

    var image = document.getElementsByClassName('back-grass')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 2
    })
    var image = document.getElementsByClassName('front-grass')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 1.4
    })
    var image = document.getElementsByClassName('desk')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 1.8
    })
    var image = document.getElementsByClassName('green-table')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 1.4
    })
    var image = document.getElementsByClassName('wall')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 1.5
    })
    var image = document.getElementsByClassName('lamp-post')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 2
    })
    var image = document.getElementsByClassName('polaroid')
    var instance = new SimpleParallax(image, {
      overflow: true,
      scale: 1.2
    })
  }
})

// left: 37, up: 38, right: 39, down: 40,
// spacebar: 32, pageup: 33, pagedown: 34, end: 35, home: 36
var keys = { 37: 1, 38: 1, 39: 1, 40: 1 }

function preventDefault (e) {
  e = e || window.event
  if (e.preventDefault) e.preventDefault()
  e.returnValue = false
}

function preventDefaultForScrollKeys (e) {
  if (keys[e.keyCode]) {
    preventDefault(e)
    return false
  }
}

function disableScroll () {
  if (window.addEventListener)
  // older FF
  { window.addEventListener('DOMMouseScroll', preventDefault, false) }
  document.addEventListener('wheel', preventDefault, { passive: false }) // Disable scrolling in Chrome
  window.onwheel = preventDefault // modern standard
  window.onmousewheel = document.onmousewheel = preventDefault // older browsers, IE
  window.ontouchmove = preventDefault // mobile
  document.onkeydown = preventDefaultForScrollKeys
}

function enableScroll () {
  if (window.removeEventListener) { window.removeEventListener('DOMMouseScroll', preventDefault, false) }
  document.removeEventListener('wheel', preventDefault, { passive: false }) // Enable scrolling in Chrome
  window.onmousewheel = document.onmousewheel = null
  window.onwheel = null
  window.ontouchmove = null
  document.onkeydown = null
}
</script>
`
