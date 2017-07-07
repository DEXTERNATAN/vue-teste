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

<style lang="scss">
  @import 'assets/styles/app.scss'
</style>