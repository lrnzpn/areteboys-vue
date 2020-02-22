<template>
  <div id="header">
    <div class="center-wrapper">
      <div class="logo-container">
        <div class="logo-wrapper">
          <img src="../assets/icons/logo.svg" alt="AB" />
          <span>AB Research Management System</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
#header {
  background-color: $black;
  position: fixed;
  z-index: 999;
  width: 100%;
  .logo-container {
    width: inherit;
    padding: 1rem 0;

    .logo-wrapper {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      text-align: center;
      width: 100%;

      span {
        color: $white;
        margin-left: 3%;
      }
    }
  }
}
</style>
