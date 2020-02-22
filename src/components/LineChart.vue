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
  },
  extends: Line,
  mixins: [reactiveProp],
  props: {
    chartdata: {
      type: Object,
      default: null
    },
    options: {
      type: Object,
      default: null
    },
  },
  mounted () {
    this.renderChart(this.chartData, this.options)
  },

}
</script>

<style>

</style>
