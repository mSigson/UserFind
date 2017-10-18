import Vue from 'vue'

<template>
  <div id="app">
    <Head></Head>
    <main class="mainContainer clearfix">
      <div class="wrapper">
        <RandomPeople :getSelectedUsers="getSelectedUsers" ></RandomPeople>
        <SelectedUsers v-if="showSelectedUsers === true" :selectedUsers="selectedUsers" :submitUsers="submitUsers"></SelectedUsers>
      </div>
    </main>
    <Foot></Foot>
  </div>
</template>

<script>

import Head from './components/Head'
import RandomPeople from './components/RandomPeople'
import SelectedUsers from './components/SelectedUsers'
import Foot from './components/Foot'

export default {
  name: 'app',
  components: {
    Head,
    RandomPeople,
    SelectedUsers,
    Foot
  },
  data: function () {
    return {
      selectedUsers: [],
      showSelectedUsers: false
    }
  },
  methods: {
    getSelectedUsers: function (selectedUsers) {
      this.selectedUsers = selectedUsers

      if (this.selectedUsers.length > 0) {
        this.showSelectedUsers = true
      }
    },
    submitUsers: function () {
      this.selectedUsers.length = 0
      this.showSelectedUsers = false
      console.log(this.selectedUsers)
    }
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
