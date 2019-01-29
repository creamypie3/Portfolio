<template>
  <div class="home">
    <b-container>
      <b-row>
        <b-col>
          <img alt="Vue logo" src="../assets/logo.png">
          <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

export default Vue.extend({
  name: 'home',
  components: {
    HelloWorld
  }
})
</script>
