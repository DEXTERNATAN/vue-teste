<template>
  <div id="app">
    <div class="header">
      <HeaderPages></HeaderPages>
    </div>
    <div class="container">
      <router-view></router-view>    
    </div>
    <div class="footer">
      <FooterPages></FooterPages>
    </div>
  </div>
</template>

<script>

import HeaderPages from './components/HeaderPages.vue'
import FooterPages from './components/FooterPages.vue'
import Alert from './components/Alert.vue'


export default {
  components: {
    HeaderPages,
    FooterPages,
    Alert
  },
  name: 'app',
  data () {
    return {
      msg: 'VUE TESTE...'
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