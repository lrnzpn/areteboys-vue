<template>
  <div id="sidenav">
    <div class="nav-menu">
      <router-link to="/">
        <div class="nav-link">
          <img src="../assets/icons/dashboard.png" alt="" />
          <span>Dashboard</span>
        </div>
      </router-link>
      <router-link to="/settings">
        <div class="nav-link">
          <img src="../assets/icons/settings.png" alt="" />
          <span>Settings</span>
        </div>
      </router-link>
      <router-link to="/import">
        <div class="nav-link">
          <img src="../assets/icons/input.png" alt="" />
          <span>Import</span>
        </div>
      </router-link>
      <router-link to="/">
        <div class="nav-link">
          <img src="../assets/icons/logout.png" alt="" />
          <span>Log out</span>
        </div>
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
  padding: 7.5rem 0;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;

  a {
    color: $white;
    width: 100%;
    margin-bottom: 20px;
    border-radius: 10px;

    &:hover {
      background-color: rgba(0, 0, 0, 0.5);
    }

    .nav-link {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      margin: 0.5em 1em;
    }
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
