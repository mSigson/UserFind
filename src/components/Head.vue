import Vue from 'vue'

<template>
  <header>
    <div class="wrapper">
      <h1>{{ msg }}</h1>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Head',
  data () {
    return {
      msg: 'Roll Em'
    }
  }
}
</script>

// <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
