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
          <b-form-group id="input-group-3" label="Municipality/City:" label-for="input-3">
            <b-form-input
              id="input-3"
              required
              placeholder="Enter City"
              v-model="form.municipality_city"
            ></b-form-input>
          </b-form-group>
          <b-form-group id="input-group-4" label="Region:" label-for="input-4">
            <b-form-input id="input-4" required placeholder="Enter Region" v-model="form.region"></b-form-input>
          </b-form-group>
          <b-form-group id="input-group-5" label="Sample Type:" label-for="input-5">
            <b-form-input id="input-5" required placeholder="Enter Type" v-model="form.sample_type"></b-form-input>
          </b-form-group>
          <b-form-group id="input-group-6" label="Sample Description:" label-for="input-6">
            <b-form-textarea
              id="input-6"
              required
              placeholder="Enter Description"
              v-model="form.sample_description"
            ></b-form-textarea>
          </b-form-group>

          <div class="checkbox-container">
            <b-form-group id="input-group-7" label-for="input-7">
              <b-form-checkbox
                id="checkbox-1"
                v-model="form.in_lab"
                name="checkbox-1"
                value="true"
                unchecked-value="false"
              >In Lab?</b-form-checkbox>
            </b-form-group>

            <b-form-group id="input-group-8" label-for="input-8">
              <b-form-checkbox
                id="checkbox-2"
                v-model="form.is_significant"
                name="checkbox-2"
                value="true"
                unchecked-value="false"
              >Is Significant?</b-form-checkbox>
            </b-form-group>
          </div>

          <b-form-group id="input-group-9" label="Photo Url:" label-for="input-9">
            <b-form-input
              id="input-9"
              required
              placeholder="Enter url"
              v-model="form.photo_main_url"
            ></b-form-input>
          </b-form-group>

          <div class="btn-container">
            <b-button type="submit" id="submit-button">Submit</b-button>
          </div>
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
        municipality_city: "",
        region: "",
        sample_type: "",
        sample_description: "",
        in_lab: "",
        is_significant: "",
        photo_main_url: ""
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
  z-index: 10000;
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
  height: 90vh;
  width: 60vw;
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

.form-group {
  margin: 0.5em;
}

.checkbox-container {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

.btn-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>