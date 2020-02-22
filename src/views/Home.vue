<template>
  <div class="home">
    <dashboard />

    <!-- for testing: -->
    <!-- <form-component formType="inputData"/> -->
  </div>
</template>

<script>
import Dashboard from '../views/Dashboard'
import Form from '../components/Form'
export default {
  name: "Home",
  components: {
    Dashboard,
    FormComponent: Form,
  }
};
</script>

<style scoped lang="scss">
</style>
