<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>

<script>
import { ref, onMounted } from 'vue'
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
if (squirrel.value[i].hasOwnProperty(primary_fur_color)
/* && */) //does it have primary fur color & is that entrys fur color not already included
//if not included, append fur color, push 1 to color numbers
//2 lists

//second if, does it have primary fur color and is that color included
//if included, find index of that color in colors list, then colorNumbers[index]+=1
{


}
export default {
  name: 'BarChart',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: ['Black', 'Brown', 'Cinnamon'],
        datasets: [{ data: [0, 0, 0] }]
      },
      chartOptions: {
        responsive: true
      }
    }
  }
}
</script>
