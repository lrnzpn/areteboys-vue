<template>
  <div id="app">
    <Header />
    <Navigation />
    <div class="header-spacer"></div>
    <router-view />
  </div>
</template>

<script>
import Header from "./components/Header";
import Navigation from "./components/Navigation";
import Vue from 'vue'
import { BootstrapVue, BootstrapVueIcons } from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue)
Vue.use(BootstrapVueIcons)

export default {
  components: {
    Header: Header,
    Navigation: Navigation
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro&display=swap');
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
