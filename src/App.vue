import Vue from 'vue'

<template>
  <div id="app">
    <Head></Head>
    <main class="mainContainer clearfix">
      <RandomPeople></RandomPeople>
    </main>
    <Foot></Foot>
  </div>
</template>

<script>

import Head from './components/Head'
import RandomPeople from './components/RandomPeople'
import Foot from './components/Foot'

export default {
  name: 'app',
  components: {
    Head,
    RandomPeople,
    Foot
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
