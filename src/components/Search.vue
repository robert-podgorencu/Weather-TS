<template>
    <div>
        <label>
            Search
            <input id="search-bar" type="text" placeholder="Enter Location" v-model="inputText">
        </label>
        <button id="submit-button" v-on:click="searchLocation">
            Search
        </button>
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { useWeatherStore } from "../stores/store.js"

const weatherStore = useWeatherStore()

let inputText = ref("");

function searchLocation():void {
    weatherStore.fetchLocationData(inputText.value);
}

</script>

<style scoped>
label {
    font-size: 20px;
}

button {
    background-color: white;
    color: black;
    border: 2px solid #555555;
    height: 40px;
    width: 60px;
    cursor: pointer;
    margin-left: 10px;
}

button:hover {
    background-color: #555555;
    color: white;
}

#search-bar {
    width: 40%;
    margin-top: 20px;
    margin-bottom: 20px;
    padding: 10px;
}
</style>