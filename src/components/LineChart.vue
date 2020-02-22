<script>
import { Line, mixins } from 'vue-chartjs'
const { reactiveProp } = mixins

export default {
  data() {
  // options: {
  //       scales: {
  //           xAxes: [{
  //               type: 'time',
  //               time: {
  //                   unit: 'year'
  //               },
  //               distribution: 'series'
  //           }]
  //       }
  //   }
  options: {
    return {
    fill: false,
    backgroundColor: 'rgba(0, 0, 0, 0.0)',
    legend: {
    display: false,
    }

}
  }
  },
  extends: Line,
  mixins: [reactiveProp],
  props: {
    chartdata: {
      type: Object,
      default: null
    },
    // options: {
    //   type: Object,
    //   default: null
    // },
  },
  mounted () {
    this.renderChart(this.chartData, this.options)
  },

}
</script>

<style>

</style>
