<template>
  <div></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const squirrel = ref('')
async function getSquirrelData() {
  let response = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json')
  let data = await response.json()
  squirrel.value = data
  console.log(squirrel.value)
}

onMounted(() => {
  getSquirrelData()
})
</script>

<style scoped></style>
