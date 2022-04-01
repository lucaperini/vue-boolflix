<template>
  <div id="app">
    <Header />
    <!-- <Main /> -->
  
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
// import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    // Main,
    
  }
}
</script>

<style lang="scss">
@import './src/styles/style.scss';
#app {
}
</style>
