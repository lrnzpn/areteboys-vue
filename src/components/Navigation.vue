<template>
  <div id="sidenav">
    <div class="nav-menu">
      <router-link to="/" class="sidebar-item">
        <img src="../assets/icons/dashboard.svg" alt="" />
        <span>Dashboard</span>
      </router-link>
      <router-link to="/settings" class="sidebar-item">
        <img src="../assets/icons/settings.svg" alt="" />
        <span>Settings</span>
      </router-link>
      <router-link to="/import" class="sidebar-item">
        <img src="../assets/icons/input-1.svg" alt="" />
        <span>Import</span>
      </router-link>
      <router-link to="/" class="sidebar-item">
        <img src="../assets/icons/logout.svg" alt="" />
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
  background-color: $main-secondary;
  position: fixed;
  z-index: 99;
  width: 20vw;
  height: 100vh;
}

.router-link-exact-active {
  /* background-color: rgba(0, 0, 0, 0.5); */
}

img {
  padding-right: 10px;
}

.sidebar-item:hover {
  background-color: #213f4a;
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
