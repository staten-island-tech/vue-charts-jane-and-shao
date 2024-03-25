<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartOptions" v-if="loaded"/>
</template>


<script>
import { Bar, getDatasetAtEvent } from 'vue-chartjs'
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
    // chartData: null,
    chartOptions: {
      labels: [ ],
      datasets:[ ]
    }
  }),
mounted() {
  async function getData(){
    this.loaded = false;


    try {
      const response = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json?limit=10');
      let data = await response.json();
      const rabies = []
        data.forEach((sq)=>
        rabies.push(sq.rabies))
        this.chartOptions.labels = rabies
        this.chartOptions.datasets = [20, 39123, 73, 27]
        
    } catch (e) {
      console.error(e)
    }
    
    this.loaded = true 
  }
  getData()
}

}

  
</script>


