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
            <div>map here</div>
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
    </div>
    <div id="viz"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      samplesSubmitted: 0,
      inProgress: 0,
      relevantSamples: 0,
      irrelevantSamples: 0
    };
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
  margin-left: 20vw;
  width: 80vw;
}
#statistics {
  margin: 0 auto;
}
#stats-container {
  display: flex;
  justify-content: space-between;
  width: 70vw;
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
  width: 80vw;
}

.viz-container {
  width: 70vw;
  display: flex;
  justify-content: space-around;
  margin: 0 auto;
  height: 75vh;
  font-size: 27.79px;
}
</style>
