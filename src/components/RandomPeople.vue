import Vue from 'vue'

<template>
  <section class="randomPeople">
    <ul class="randomUsers">
      <li v-for="user in sortedUsers" :key="user.id.value" class="notSelected" v-on:click="select(user)">
        {{ user.name.first}} {{ user.name.last}} {{ user.email }}
        {{ user.dob }}
      </li>
    </ul>
    <div class="buttonContainer">
      <button v-on:click="getMoreUsers">Roll</button>
      <button v-on:click="confirmUsers" >Add Users</button>
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
      isActive: false,
      submitBtnDisabled: true
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
  created: function () {
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
      // this.selectedUsers.push(this.users[0])
      this.sortedUsers = this.users
    })
  },
  mounted: function () {
    this.sortedUsers[0].hasClass('selected')
  }
}
</script>

<style>
  .selected {
    background: #E5A3AD;
    color: white;
  }
</style>
