<template>
  <div id="app">
    <h1>Vue.js boilerplate</h1>
    <div v-for="event in events">
      <h2><a :href="event.html_url">{{event.full_name}}</a></h2>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data () {
    return {
      url: 'https://api.github.com/search/repositories',
      events: []
    }
  },
  created() {
    axios.get(this.url, {
      params: {
        q: 'vuejs'
      }
    })
    .then(response => this.events = response.data.items)
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
