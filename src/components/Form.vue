<template>
  <div id="form-wrapper">
    <div id="form-container">
      <h1 v-if="formType==='logIn'">Log In</h1>
      <div class="form-header" v-else-if="formType==='inputData'">
        <h1>Input Data</h1>
        <button @click="closeInput">X</button>
      </div>

      <div v-if="formType==='logIn'">
        <b-form>
          <b-form-group id="input-group-1" label="Username:" label-for="input-1">
            <b-form-input id="input-1" required placeholder="Enter username"></b-form-input>
          </b-form-group>
        </b-form>
        <b-form>
          <b-form-group id="input-group-2" label="Password:" label-for="input-2">
            <b-form-input id="input-2" required placeholder="Enter password" type="password"></b-form-input>
          </b-form-group>
        </b-form>
      </div>
      <div v-else-if="formType==='inputData'">
        <b-form @submit.prevent="postData">
          <b-form-group id="input-group-3" label="Sample Type:" label-for="input-3">
            <!-- <b-form-input
            id="input-1" required placeholder="Enter sample
            "></b-form-input>-->
            <b-form-select
              class="mb-2 mr-sm-2 mb-sm-0"
              :value="null"
              :options="{ '1': 'One', '2': 'Two', '3': 'Three' }"
              id="inline-form-custom-select-pref"
              v-model="form.sample"
            >
              <template v-slot:first>
                <option :value="null">Choose...</option>
              </template>
            </b-form-select>
          </b-form-group>
          <b-form-group id="input-group-4" label="Location:" label-for="input-4">
            <b-form-input
              id="input-4"
              required
              placeholder="Enter location"
              v-model="form.location"
            ></b-form-input>
          </b-form-group>
          <b-form-group id="input-group-5" label="Description:" label-for="input-5">
            <b-form-input
              id="input-5"
              required
              placeholder="Enter description"
              v-model="form.description"
            ></b-form-input>
          </b-form-group>
          <b-button type="submit" id="submit-button">Submit</b-button>
        </b-form>
      </div>
    </div>
  </div>
</template>

<script>
import { BootstrapVue, BootstrapVueIcons } from "bootstrap-vue";

export default {
  data() {
    return {
      form: {
        sample: "",
        location: "",
        description: ""
      }
    };
  },
  props: ["formType", "title"],
  methods: {
    closeInput() {
      document.getElementById("form-wrapper").style.display = "none";
    },
    postData(e) {
      document.getElementById("form-wrapper").style.display = "none";
      this.$emit("postData", this.form);
    }
  }
};
</script>

<style scoped lang="scss">
#form-wrapper {
  position: fixed;
  z-index: 998;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow-y: hidden;
}

#form-container {
  background-color: $main-blue;
  color: white;
  text-align: left;
  height: 70vh;
  width: 50vw;
  margin-left: 20vw;
  padding-left: 5%;
  padding-right: 5%;
  padding-top: 20px;
  border-radius: 15px;

  .form-header {
    display: flex;
    justify-content: space-between;
    align-items: center;

    button {
      border-radius: 7.5px;
    }
  }
}
#submit-button {
  background-color: $main-secondary;
}
</style>