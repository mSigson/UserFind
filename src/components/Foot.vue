import Vue from 'vue'

<template>
  <footer>
    <div class="wrapper">
      <p>{{ msg }}</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Foot',
  data () {
    return {
      msg: 'Developed by Maren Sigson'
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
