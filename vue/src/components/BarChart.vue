<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartOptions" v-if="loaded"/>
</template>


<script>
<<<<<<< HEAD
import { Bar, getDatasetAtEvent } from 'vue-chartjs'
=======
import { ref } from 'vue'
import { Bar } from 'vue-chartjs'
>>>>>>> main-THE-REAL-ONE
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
<<<<<<< HEAD


export default {
  name: 'BarChart',
  components: { Bar },
  data: () => ({
    loaded: false,
    // chartData: null,
    chartOptions: {
      labels: [ ],
      datasets:[ ]
=======
export default {
  name: 'BarChart',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: colors,
        datasets: [{ data: colorNumbers }]
      },
      chartOptions: {
        responsive: true
      }
>>>>>>> main-THE-REAL-ONE
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
<<<<<<< HEAD

}

  
=======
const squirrel = ref('')
async function getSquirrelData() {
  let response = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json')
  let data = await response.json()
  console.log(data)
  return data
}

squirrel.value = await getSquirrelData()

const colors = []
const colorNumbers = []
for (let i = 0; i < squirrel.value.length; i++) {
  if (
    squirrel.value[i].hasOwnProperty('primary_fur_color') &&
    !colors.includes(squirrel.value[i].primary_fur_color)
  ) {
    colors.push(squirrel.value[i].primary_fur_color)
    colorNumbers.push(1)
  } else if (squirrel.value[i].hasOwnProperty('primary_fur_color')) {
    let index = colors.indexOf(squirrel.value[i].primary_fur_color)
    colorNumbers[index]++
  }
}
console.log(colorNumbers)
>>>>>>> main-THE-REAL-ONE
</script>


