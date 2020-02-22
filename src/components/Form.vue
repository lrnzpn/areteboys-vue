<template>
  <div id="container">
      <h1 v-if="formType==='logIn'">Log In</h1>
      <h1 v-else-if="formType==='inputData'">Input Data</h1>
    <div v-if="formType==='logIn'"><b-form>
    <b-form-group id="input-group-1" label="Username:" label-for="input-1">
    <b-form-input id="input-1" required placeholder="Enter username">
    </b-form-input>
    </b-form-group>
    </b-form>
    <b-form>
    <b-form-group id="input-group-2" label="Password:" label-for="input-2">
    <b-form-input id="input-2"  required placeholder="Enter password" type="password"></b-form-input>
    </b-form-group>
    </b-form>
    </div>
    <div v-else-if="formType==='inputData'">
        <b-form-group
        id="input-group-3" 
        label="Sample Type:" 
        label-for="input-3">
            <!-- <b-form-input
            id="input-1" required placeholder="Enter sample
            "></b-form-input> -->
            <b-form-select
      class="mb-2 mr-sm-2 mb-sm-0"
      :value="null"
      :options="{ '1': 'One', '2': 'Two', '3': 'Three' }"
      id="inline-form-custom-select-pref"
    >
      <template v-slot:first>
        <option :value="null">Choose...</option>
      </template>
    </b-form-select>
        </b-form-group>
        <b-form-group
        id="input-group-4" 
        label="Location:" 
        label-for="input-3">
            <b-form-input
            id="input-1" required placeholder="Enter location
            "></b-form-input>
        </b-form-group>
        <b-form-group
        id="input-group-4" 
        label="Description:" 
        label-for="input-4">
            <b-form-input
            id="input-1" required placeholder="Enter description
            "></b-form-input>
        </b-form-group>
    </div>
    <b-button type="submit" id="submit-button">Submit</b-button>
  </div>
</template>

<script>
import { BootstrapVue, BootstrapVueIcons } from 'bootstrap-vue'

export default {
  props: ["formType", "title"]
};
</script>

<style scoped lang="scss">

#container{
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
}
#submit-button{
    background-color: $main-secondary;
}
</style>