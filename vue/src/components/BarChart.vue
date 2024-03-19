<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" v-if="loaded"/>
</template>

<script>
import { Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data: () => ({
    loaded: false,
    chartData: null
      }),
     async mounted (){
      this.loaded = false 

      try {
        const {color} = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json')
        this.chartdata = color

        this.loaded = true
      } catch (e){
        console.error(e)
      }
     }
}
</script>
