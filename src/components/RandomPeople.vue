import Vue from 'vue'

<template>
  <section class="randomPeople">
    <ul class="users">
      <li v-for="user in sortedUsers" :key="user.id.value" name="user" class="notSelected" v-on:click="select(user)">
        {{ user.name.first}} {{ user.name.last}}
        {{ user.dob }}
        {{ user.email }}
      </li>
    </ul>
    <div class="buttonContainer">
      <button v-on:click="getMoreUsers">Roll</button>
      <button v-on:click="confirmUsers">Add Users</button>
    </div>
  </section>
</template>

<script>

export default {
  data: function () {
    return {
      name: 'RandomPeople',
      users: [],
      sortedUsers: [],
      selectedUsers: [],
      isActive: false
    }
  },
  methods: {
    getMoreUsers: function () {
      this.$http.get('https://randomuser.me/api/?results=5')
      .then(function (data) {
        this.users = data.body.results
      })
      .then(function () {
        this.users.sort((a, b) => {
          a.className = 'selected'
          return new Date(a.dob) - new Date(b.dob)
        })
      })
      .then(function () {
        this.sortedUsers = this.users
      })
    },
    select: function (user) {
      if (event.target.className === 'notSelected') {
        event.target.className = 'selected'
        if (!this.selectedUsers.includes(user)) {
          this.selectedUsers.push(user)
        }
      } else {
        event.target.className = 'notSelected'
        let i = this.selectedUsers.indexOf(user)
        if (i !== -1) {
          this.selectedUsers.splice(i, 1)
        }
      }
    },
    confirmUsers: function (event) {
      this.getMoreUsers()
      this.$parent.getSelectedUsers(this.selectedUsers)
    }
  },
  mounted: function () {
    this.$http.get('https://randomuser.me/api/?results=5')
    .then(function (data) {
      this.users = data.body.results
    })
    .then(function () {
      this.users.sort((a, b) => {
        return new Date(a.dob) - new Date(b.dob)
      })
    })
    .then(function () {
      this.users[0].className = 'selected'
      this.sortedUsers = this.users
    })
  }
}
</script>

<style>
  .selected {
    border: 2px solid pink;
  }
</style>
