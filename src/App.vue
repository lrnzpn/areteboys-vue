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

export default {
  components: {
    Header: Header,
    Navigation: Navigation
  }
};
</script>

<style lang="scss">
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
