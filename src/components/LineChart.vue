<script>
import { Line, mixins } from 'vue-chartjs'
import moment from 'moment'
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
  props: ['options'],
  mounted () {
    this.renderChart(this.chartData, this.options)
  },

}
</script>

<style>

</style>
