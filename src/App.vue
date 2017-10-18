import Vue from 'vue'

<template>
  <div id="app">
    <Head></Head>
    <main class="mainContainer clearfix">
      <div class="wrapper clearfix">
        <RandomPeople :getSelectedUsers="getSelectedUsers" ></RandomPeople>
        <section class="selectedUsersContainer">
          <SelectedUsers v-if="showSelectedUsers === true" :selectedUsers="selectedUsers" :submitUsers="submitUsers"></SelectedUsers>
          <button v-on:click="submitUsers">Submit Users</button>
        </section>
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
    }
  }
}
</script>

<style>

{/* global */}

ul {
  list-style: none;
  padding: 20px 10px;
  border: 2px solid #E5A3AD;
}

ul li {
  padding: 5px 0;
}

button {
  background: #E5A3AD;
  color: white;
  border: none;
  padding: 10px 20px;
  border: 2px solid #E5A3AD;  
  &:hover {
    background: white;
    color: #E5A3AD;
  }
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  word-wrap: break-word;  
}

.wrapper {
  width: 90%;
  margin: 0 auto;
}

header, footer {
  background: #E5A3AD;
  padding: 5px;
  color: white;
}

main {
  padding: 20px;
}

main .wrapper {
  display: flex;
  justify-content: space-between;
}

.randomPeople, .selectedUsersContainer {
  padding: 2px 30px;
  border: 2px solid #E5A3AD;
  box-shadow: 2px 2px 5px #888888;  
}

.randomPeople {
  width: 65%;
}

.selectedUsersContainer {
  width: 25%;
  position: relative;
}

.selectedUsersContainer button {
  position: absolute;
  bottom: 0;
}

</style>
