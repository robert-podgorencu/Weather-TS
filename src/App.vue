<script setup lang="ts">
import CurrentWeather from './components/CurrentWeather.vue'
import Search from './components/Search.vue'
import { useWeatherStore } from "./stores/store.js"
import { storeToRefs } from "pinia";

const weatherStore = useWeatherStore()
const { getWeatherData } = storeToRefs(weatherStore)
</script>

<template>
  <Search />
  <CurrentWeather v-if="getWeatherData !== null" />
</template>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  width: 100%;
  margin-top: 10%;
  text-align: center;
}
</style>
