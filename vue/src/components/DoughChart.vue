<template>
    <Doughnut :data="chartData" :options="options" />
</template>
  
<script lang="ts">
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
import { Doughnut } from 'vue-chartjs'


ChartJS.register(ArcElement, Tooltip, Legend)

export default {
    name: 'App',
    components: {
        Doughnut
    },
    data() {
        chartData: {
            labels: colors,
                datasets: [
                    {
                        backgroundColor: ['#41B883', '#E46651', '#00D8FF', '#DD1B16'],
                        data: colornumbers
                    }
                ]
        },

        const options = {
            responsive: true,
            maintainAspectRatio: false
        }

    }
}
</script>