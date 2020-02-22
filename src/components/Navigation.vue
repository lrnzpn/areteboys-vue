<template>
  <div id="sidenav">
    <div class="nav-menu">
      <router-link to="/">
        <img src="../assets/icons/dashboard.png" alt="" />
        <span>Dashboard</span>
      </router-link>
      <router-link to="/settings">
        <img src="../assets/icons/settings.png" alt="" />
        <span>Settings</span>
      </router-link>
      <router-link to="/import">
        <img src="../assets/icons/input.png" alt="" />
        <span>Import</span>
      </router-link>
      <router-link to="/">
        <img src="../assets/icons/logout.png" alt="" />
        <span>Log out</span>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
#sidenav {
  background-color: #ccc;
  position: fixed;
  z-index: 99;
  width: 200px;
  height: 100vh;
}

.router-link-exact-active {
  background-color: rgba(0, 0, 0, 0.5);
}

.nav-menu {
  height: 100%;
  padding: 7.5rem 20%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;

  a {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    color: $white;
    width: 100%;
    margin-bottom: 20px;
    padding: 0.75em;
    border-radius: 10px;
  }

  img {
    height: 1.5em;
    width: 1.5em;
  }

  span {
    margin-left: 3%;
  }
}
</style>
