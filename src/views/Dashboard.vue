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
          <h5 class="stat-val">{{ inProgress }}</h5>
        </div>
        <div class="stat">
          <h5 class="stat-title">Relevant Samples</h5>
          <h5 class="stat-val">{{ relevantSamples }}</h5>
        </div>
        <div class="stat">
          <h5 class="stat-title">Irrelevant Samples</h5>
          <h5 class="stat-val">{{ irrelevantSamples }}</h5>
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
            <div class="chart1">
              <!-- <bar-chart :chartdata='dummyData' options=''></bar-chart> -->
              <bar-chart :chart-data="datacollection">
              </bar-chart>
              <!-- <button @click="fillData()">Randomize</button> -->
            </div>
          </div>
        </div>
        <div class="viz-container viz-container-2">
          <div>
            <h5 class="viz-item">Tests</h5>
            <div>
              <line-chart>

              </line-chart>
              </div>
          </div>
          <div>
            <h5 class="viz-item>">Something</h5>
            <div>chart here</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Form from '../components/Form.vue'
import Map from '../components/Map.vue'
import BarChart from '../components/BarChart.vue'
import LineChart from '../components/LineChart.vue'
export default {
  data() {
    return {
      datacollection: null,
      samplesSubmitted: 0,
      inProgress: 0,
      relevantSamples: 0,
      irrelevantSamples: 0,
      top5artifacts: ['test','test','test','test','test'],
    };
  },

  components: {
    Form,
    MapLeaf: Map,
    BarChart,
    LineChart
  },
      mounted () {
      this.fillData()
    },
    methods: {
      fillData () {
        this.datacollection = {
          // labels: [this.getRandomInt(), this.getRandomInt()],
          labels: ['Top 5 artifacts'],
          // labels: ['test label 1', 'test label 2'],
          datasets: [
            {
              label: this.top5artifacts[0],
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()]
            }, 
            {
              label: this.top5artifacts[1],
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()]
            },
            {
              label: this.top5artifacts[2],
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()]
            },
            {
              label: this.top5artifacts[3],
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()]
            },
            {
              label: this.top5artifacts[4],
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()]
            }
          ]
        }
      },
      getRandomInt () {
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
      }
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
 .chart1 {
    max-width: 100%;
    padding-top: 40px;
    /* margin:  150px auto; */
  }

  .viz-container-2{
    margin-top: 50px;
  }
</style>
