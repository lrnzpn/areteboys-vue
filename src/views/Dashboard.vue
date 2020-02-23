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
        <div class="viz-container viz-container-1">
            <div><h5>Interactive map</h5>
            <MapLeaf /></div>
<!-- <iframe src="../Quick-Start-Leaflet-2.html" width="400" height="400"></iframe> -->
<!-- <my-map /> -->
        </div>
        <div class="viz-container viz-container-2">
          <div>
            <h5 class="viz-item">Tests</h5>
            <div class="chart2">
              <line-chart :chart-data="datacollection2">

              </line-chart>
              </div>
          </div>
          <div>
            <h5 class="viz-item">Data tested</h5>
            <div class="chart1">
              <!-- <bar-chart :chartdata='dummyData' options=''></bar-chart> -->
              <bar-chart :chart-data="datacollection1">
              </bar-chart>
              <!-- <button @click="fillData()">Randomize</button> -->
            </div>
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
import axios from "axios";
import Form from '../components/Form.vue'
import Map from '../components/Map.vue'
import BarChart from '../components/BarChart.vue'
import LineChart from '../components/LineChart.vue'
import moment from 'moment'

import 'moment'

export default {
  data() {
    return {
      datacollection1: null,
      datacollection2: null,
      samplesSubmitted: 0,
      inProgress: 0,
      relevantSamples: 0,
      irrelevantSamples: 0,
      top5artifacts: ['test','test','test','test','test'],
      months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August','September','October','November','December'],
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
      samples: [],
      top5artifacts: ['test','test','test','test','test'],
      months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August','September','October','November','December'],
    };
  },
  components: {
    Form: Form,
    MapLeaf: Map,
    BarChart,
    LineChart,
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
,
      mounted () {
      this.fillData()
    },
    methods: {
       openInputForm() {
      document.getElementById("form-wrapper").style.display = "flex";
    },
    postForm(value) {
      this.samples = [...this.samples, value];
    },
        // add(event){
        //     let current = moment()                  
        // },
  
      fillData () {
        this.datacollection1 = {
          // labels: [this.getRandomInt(), this.getRandomInt()],
          labels: ['Top 5 artifacts'],
          datasets: [
            {
              label: this.top5artifacts[0],
              backgroundColor: '#f87979',
              data: [this.getRandomInt()]
            }, 
            {
              label: this.top5artifacts[1],
              backgroundColor: '#f87979',
              data: [this.getRandomInt()]
            },
            {
              label: this.top5artifacts[2],
              backgroundColor: '#f87979',
              data: [this.getRandomInt()]
            },
            {
              label: this.top5artifacts[3],
              backgroundColor: '#f87979',
              data: [this.getRandomInt()]
            },
            {
              label: this.top5artifacts[4],
              backgroundColor: '#f87979',
              data: [this.getRandomInt()]
            }
          ]
        }

          this.datacollection2 = {
          // labels: [this.getRandomInt(), this.getRandomInt()],
labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August','September','October','November','December'],
          datasets: [
            {
              label: '',
              backgroundColor: 'rgba(0, 0, 0, 0.0)',
              data: [
                {x:this.months[0], y:this.getRandomInt()},
                {x:this.months[1], y:this.getRandomInt()},
                {x:this.months[2], y:this.getRandomInt()},
                {x:this.months[3], y:this.getRandomInt()},
                {x:this.months[4], y:this.getRandomInt()},
                {x:this.months[5], y:this.getRandomInt()},
                {x:this.months[6], y:this.getRandomInt()},
                {x:this.months[7], y:this.getRandomInt()},
                {x:this.months[8], y:this.getRandomInt()},
                {x:this.months[9], y:this.getRandomInt()},
                {x:this.months[10], y:this.getRandomInt()},
                {x:this.months[11], y:this.getRandomInt()},

                ]

            }, 
          ]
        }

//         this.datacollection2 = {
//           datasets: [{

//           data:[
//             {x: 1980,
//             y: 50},]},

// {data:
//             [{x: 1983, 
//             y: 69}]}
//           ]
//         }
      },
      getRandomInt () {
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
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
}};
</script>

<style scoped lang="scss">
h5 {
  margin: 0;
}

h1 {
  color: $dashboard-heading;
  padding-right: 85px;
}
h5 {
  color: #5aa8c8;
}

#dashboard {
  font-family: "Source Sans Pro";
  margin-left: 17vw;
  width: 85vw;
  margin-top: 40px;
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
  overflow: visible;
  padding-top: 40px;
}

.viz-container {
  width: 80vw;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
  height: 75vh;
  font-size: 27.79px;
  padding-right: 20vh;
  padding-top: 40px;
}

.viz-container-1{
  display: flex;
  text-align:center;
  justify-content: center;
  margin: 0 auto;
  width: 80vw;
}
 .chart1, .chart2 {
    max-width: 100%;
    padding-top: 40px;
    /* margin:  0 auto; */
  }

  .viz-container-2{
    margin-top: 50px;
  }

.map-item{
  text-align: center;
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
