<template>
  <div id="app">

    <appHeader v-on:menuShow="showMenu" />
    <appMenu v-if="menuShow" v-on:menuHidden="hideMenu" />

    <div class="app__container">
      <operations />
    </div>

  </div>
</template>

<script>
import appHeader from './components/appHeader.vue'
import appMenu from './components/appMenu.vue'
import operations from './components/operations.vue'

export default {
  name: 'app',
  components: {
    appHeader,
    appMenu,
    operations
  },
  data: function () {
    return {
      menuShow: false
    }
  },
  methods: {
    showMenu: function () { this.menuShow = true; },
    hideMenu: function () { this.menuShow = false;}
  }
}
</script>

<style>
body {
  overflow-x: hidden;
  box-sizing: border-box;
}
#app {
  overflow: hidden;
  font-family: 'Lato', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333333;
  margin: 0;
  padding: 0;
  border-bottom: 10px solid #333333;
  min-height: 100vh;
  position: relative;
}
.app__container {
  padding: 15px;
  max-width: 1100px;
  margin: 0 auto;
}
</style>
