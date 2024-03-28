<template>

  <header>


    <div class="wrapper">

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/bar">Bar</RouterLink>
        <RouterLink to="/donut">Donut</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />

</template>

<script setup>
import HomeView from './views/HomeView.vue'
import BarView from './views/BarView.vue'
import DonutView from './views/DonutView.vue'
</script>
