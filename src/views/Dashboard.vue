<template>
  <div id="dashboard">
    <div id="statistics">
      <h1>Statistics</h1>
      <div id="stats-container">
        <div class="stat">
          <h5 class="stat-title">Samples Submitted</h5>
          <h5 class="stat-val">{{ samplesSubmitted }}</h5>
        </div>
        <div class="stat">
          <h5 class="stat-title">In Progress</h5>
          <h5 class="stat-val">4</h5>
        </div>
        <div class="stat">
          <h5 class="stat-title">Relevant Samples</h5>
          <h5 class="stat-val">2</h5>
        </div>
        <div class="stat">
          <h5 class="stat-title">Irrelevant Samples</h5>
          <h5 class="stat-val">3</h5>
        </div>
      </div>
      <div id="viz">
        <h1>Visualization tools</h1>
        <div class="viz-container">
          <div>
            <h5 class="viz-item">Interactive map</h5>
            <MapLeaf />
          </div>
          <div>
            <h5 class="viz-item">Data tested</h5>
            <div>chart here</div>
          </div>
        </div>
        <div class="viz-container">
          <div>
            <h5 class="viz-item">Tests</h5>
            <div>chart here</div>
          </div>
          <div>
            <h5 class="viz-item">Something</h5>
            <div>chart here</div>
          </div>
        </div>
      </div>
      <div id="table">
        <h1>Raw Data</h1>
        <div class="table-btn">
          <button @click="openInputForm">Add Data</button>
        </div>
        <Form style="display:none;" formType="inputData" title="Input" v-on:postData="postForm" />

        <div class="table">
          <b-table striped hover small details-td-class tdClass :items="samples" :fields="fields"></b-table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Form from "../components/Form.vue";
import Map from "../components/Map.vue";
import axios from "axios";

export default {
  data() {
    return {
      samplesSubmitted: 0,
      inProgress: 0,
      relevantSamples: 0,
      irrelevantSamples: 0,
      fields: [
        "id",
        "municipality_city",
        "region",
        "sample_type",
        "sample_description",
        "in_lab",
        "is_significant",
        "photo_main_url"
      ],
      samples: []
    };
  },
  components: {
    Form: Form,
    MapLeaf: Map
  },
  methods: {
    openInputForm() {
      document.getElementById("form-wrapper").style.display = "flex";
    },
    postForm(value) {
      this.samples = [...this.samples, value];
    }
  },
  mounted() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    axios
      .get("http://0.0.0.0:8000/samples/api/samples/", config)
      .then(res => {
        this.samples = res.data;
        console.log(this.samples);
        this.samplesSubmitted = this.samples.length;

        let count1 = 0;
        let count2 = 0;

        for (let i = 0; i < this.samplesSubmitted; i++) {
          if (samples[i].in_lab === true) {
            count1++;
          }

          if (samples[i].is_significant === true) {
            count2++;
          }
        }

        this.inProgress = count1;
        this.isSignificant = count2;
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>

<style scoped lang="scss">
h5 {
  margin: 0;
}

h1 {
  color: $dashboard-heading;
}
h5 {
  color: #5aa8c8;
}

#dashboard {
  font-family: "Source Sans Pro";
  margin-left: 17vw;
  width: 85vw;
}
#statistics {
  margin: 0 auto;
}
#stats-container {
  display: flex;
  justify-content: space-around;
  width: 75vw;
  margin: 0 auto;
  padding-top: 20px;
  flex-direction: row;
  height: 25vh;
}

.stat {
  height: 50px;
}

.stat-title {
  font-size: 21.64px;
}

.stat-val {
  font-size: 43.29px;
}

#viz {
  width: 85vw;
}

.viz-container {
  width: 75vw;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
  height: 75vh;
  font-size: 27.79px;
  padding-right: 20vh;
  /* padding-top: 10vh; */
}

.table {
  width: 80vw;
  border: 2px solid #5aa8c8;
}

.table-btn {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
  margin-bottom: 1%;
}
</style>
