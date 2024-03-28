<template>
  <div class="donutChart">  <Doughnut :data="chartData" :options="options" /></div>

</template>

<script>
import { ref } from 'vue'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
import { Doughnut } from 'vue-chartjs'

ChartJS.register(ArcElement, Tooltip, Legend)

export default {
  name: 'DoughChart',
  components: { Doughnut },
  data() {
    return {
      chartData: {
        labels: ages,
        datasets: [
          {
            backgroundColor: ['#42b3f5', '#871a50'],
             data: ageNumbers }]
      },

      chartOptions: {
        responsive: true,
        backgroundColor: ['#871a50'],  
        maintainAspectRatio: false
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

const ages = []
const ageNumbers = []
for (let i = 0; i < squirrel.value.length; i++) {
  if (squirrel.value[i].hasOwnProperty('age') && !ages.includes(squirrel.value[i].age)) {
    ages.push(squirrel.value[i].age)
    ageNumbers.push(1)
  } else if (squirrel.value[i].hasOwnProperty('age')) {
    let index = ages.indexOf(squirrel.value[i].age)
    ageNumbers[index]++
  }
}
</script>
