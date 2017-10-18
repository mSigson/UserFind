import Vue from 'vue'

<template>
    <ul class="selectedUsers">
      <li v-for="user in selectedUsers" :key="user.id.value" name="user">
        {{ user.email }}
      </li>
    </ul>
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