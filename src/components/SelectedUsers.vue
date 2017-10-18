import Vue from 'vue'

<template>
  <section class="selectedUsersContainer">
    <ul class="selectedUsers">
      <h2>SelectedUsers</h2>
      <li v-for="user in selectedUsers" :key="user.id.value" name="user">
        {{ user.email }}
      </li>
    </ul>
    <button v-on:click="submitUsers">Submit Users</button>
  </section>
</template>

<script>
export default {
  name: 'SelectedUsers',
  data: function () {
    return {
      selectedUsers: []
    }
  },
  methods: {
    submitUsers: function () {
      this.selectedUsers = []
      this.$parent.submitUsers()
    }
  },
  mounted: function () {
    this.selectedUsers = this.$parent.selectedUsers
  }
}
</script>