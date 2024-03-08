<template>
  <div></div>
</template>

<script setup>
import { ref, Created } from 'vue'
const sqil = ref('')
async function getsquil() {
  let res = await fetch('https://data.cityofnewyork.us/resource/vfnx-vebw.json')
  let data = await res.json()
  sqil.value = data.results
}
Created(() => {
  getsqil()
})
</script>

<style scoped></style>
