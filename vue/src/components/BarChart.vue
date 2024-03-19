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
    chartData: null,
    chartOptions: {} 
  }),
  async mounted() {
    this.loaded = false;


    try {
      const response = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json');
      if (response.ok) {
        const data = await response.json();
        this.chartData = data;
        this.loaded = true;
      } else {
        console.error('Failed to fetch data:', response.status);
      }
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  }
}
</script>
