<template>
  <Doughnut :data="chartData" :options="options" />
</template>

<script lang="ts">
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
import { Doughnut } from 'vue-chartjs'


ChartJS.register(ArcElement, Tooltip, Legend)

export default {
    name: 'DoughChart',
    components: {
        Doughnut
    },
    data() {
        return{
        chartData: {
            labels: colors,
                datasets: [{data: colornumbers}]
        },

        const options = {
            responsive: true,
            maintainAspectRatio: false
        }

    }
}
}
</script>
