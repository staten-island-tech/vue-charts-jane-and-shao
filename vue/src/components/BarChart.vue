<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>

<script>
import { ref } from 'vue'
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
  data() {
    return {
      chartData: {
        labels: colors,
        datasets: [{ data: colorNumbers }]
      },
      chartOptions: {
        responsive: true
      }
    }
  }
}
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
</script>
