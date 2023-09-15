<template>
  <div class="card" >
    <div class="top-row">
      <h2 class="city">{{ getWeatherData!.name }}</h2>
      <img alt="weather" class="weather-icon" :src="returnImageUrl()">
      <h2 class="temperature">{{ Math.round(getWeatherData!.main.temp) }}°C</h2>
      <p class="weather-description">
        {{ getWeatherData!.weather[0].description }}
      </p>
    </div>

    <div class="bot-row">
      <div class="parameter-row">
        <h3 class="parameter-label">Details</h3>
      </div>
      <ul class="details">
        <li class="parameter-row">
          <span class="parameter-label">Feels like: </span>
          <span class="parameter-value">
            {{ Math.round(getWeatherData!.main.feels_like) }}°C
          </span>
        </li>
        <li class="parameter-row">
          <span class="parameter-label">Wind: </span>
          <span class="parameter-value">
            {{ getWeatherData!.wind.speed }} m/s
          </span>
        </li>
        <li class="parameter-row">
          <span class="parameter-label">Humidity: </span>
          <span class="parameter-value">
            {{ getWeatherData!.main.humidity }}%
          </span>
        </li>
        <li class="parameter-row">
          <span class="parameter-label">Pressure: </span>
          <span class="parameter-value">
            {{ getWeatherData!.main.pressure }} hPa
          </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { storeToRefs } from "pinia";
import { useWeatherStore } from "../stores/store.js"

const weatherStore = useWeatherStore()
const { getWeatherData } = storeToRefs(weatherStore)

function returnImageUrl():string {
  if (getWeatherData.value !== null) {
    return `icons/${getWeatherData.value.weather[0].icon}.png`;
  }
  return ""
}

</script>

<style scoped>
.bot-row {
  width: 200px;
  display: inline-block;
  text-align: center;
}

.parameter-value {
  float: right;
}

ul {
  padding: 0;
  list-style: none;
}

li {
  margin-bottom: 10px;
  text-align: left;
}
</style>