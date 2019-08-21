<template>
  <div class="home">
    <section>
    <b-container fluid class="p-0">
      <b-row class="hero">
        <b-col sm="12" md="12" cols="12" offset="0">
            <figure class="background">
              <img class="background-sky" src="../../public/img/Splash/splash.png" />
            </figure>
            <figure class="foreground">
              <img class="character" src="../../public/img/Splash/splash3.png" />
            </figure> 
            <article>
              <img class="back-grass" src="../../public/img/Splash/splash1.png" />
              <img class="front-grass" src="../../public/img/Splash/splash2.png" />
              <img class="lamp-post" src="../../public/img/Splash/splash5.png" /> 
              <img class="green-table" src="../../public/img/Splash/splash4.png" />
              <img class="wall" src="../../public/img/Splash/room.png" />
              <img class="polaroid" src="../../public/img/Splash/polaroid.png" />
              <img class="desk" src="../../public/img/Splash/desk.png" />
              

            </article> 
        </b-col>
      </b-row>
    </b-container>
     </section>
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
      <b-row class="height-50" no-gutters="true" v-for="(page, key, index) in json" :key="page.id">
        <b-col sm="12" md="6" :class="{'order-md-2': index % 2 == 0 }">
          <a :href="'/project/' + key">
            <img :src="'/img' + page.featuredImage" style="background-color:" page.color />
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
  </div>
</template>

<style lang="scss">
@import "../assets/variables.scss";
img {
  width: 100%;
}
.height-50 {
  display: block;
  min-height: 50vh;
  max-height: 80vh;
  background: white;
  color: black;
  a {
    color: black;
    width: 100%;
    &:hover {
      color: $primary-blue;
      text-decoration: none;
    }
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
.hero {
  //overflow: hidden;


  .back-grass {
    position: relative;
    z-index: 1;
    top: 50px;
  }
  .front-grass{
    position: relative;
    z-index: 2;
    top: 100px;
  }
  .lamp-post {
    position: relative;
    z-index: 3;
  }
  .green-table{
    position: relative;
    z-index: 4;
    top:150px;
  }
  .wall {
    position: relative;
    z-index: 1;
    top: 800px;
  }
  .desk{
    position: relative;
    z-index: 4;
    top: 900px;
  }
  .polaroid{
    position: relative;
    z-index: 4;
    top: 800px;
  }
 .foreground {
   z-index: 3;
 }
  figure{
  align-items: center;
  height: 100vh;
  margin: 0;
  width: 100%;
  justify-content: center;
  top: $top-offset;
    .background{
      z-index: -1;
    }
  img {
    left:0px;
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
  z-index:1;
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
import Vue from "vue";
import HelloWorld from "@/components/HelloWorld.vue";
import simpleParallax from "simple-parallax-js";
var json = require("@/static/content.json");
// @ is an alias to /src

export default Vue.extend({
  name: "home",
  components: {
    HelloWorld
  },
  data() {
    return {
      json: {}
    };
  },
  mounted() {
    this.json = json;
    console.log(json);
    
    var image = document.getElementsByClassName("back-grass");
    var instance = new simpleParallax(image, {
      overflow: true,
      scale: 1.8
    });
    var image = document.getElementsByClassName("front-grass");
      var instance = new simpleParallax(image, {
        overflow: true,
        scale: 1.4
      });
    var image = document.getElementsByClassName("");
        var instance = new simpleParallax(image, {
          overflow: true,
          scale: 1.4
        });
    var image = document.getElementsByClassName("green-table");
        var instance = new simpleParallax(image, {
          overflow: true,
          scale: 1.4
      });
    var image = document.getElementsByClassName("wall");
      var instance = new simpleParallax(image, {
        overflow: true,
        scale: 2
      });
    var image = document.getElementsByClassName("lamp-post");
        var instance = new simpleParallax(image, {
          overflow: true,
          scale: 2.2
        }); 
    var image = document.getElementsByClassName("");
        var instance = new simpleParallax(image, {
          overflow: true,
          scale: 1.
      }); 
    }
  })


  
    </script>
`
