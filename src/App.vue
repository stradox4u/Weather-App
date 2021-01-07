<template>
  <div class="container">
    <app-header></app-header>
    <search-bar @data-returned="passToPanel"></search-bar>
    <weather-panel :iconUrl="iconUrl" :temperature="temperature" :feelsLike="feelsLike" :description="description" :city="city" v-if="dataReturned"></weather-panel>
  </div>
</template>

<script>
import AppHeader from './components/UI/AppHeader.vue'
import WeatherPanel from './components/weather/WeatherPanel.vue'
import SearchBar from './components/UI/SearchBar.vue'

export default {
  name: 'App',
  data() {
    return {
      weatherDataForPanel: {},
      temperature: 0,
      iconUrl: '',
      feelsLike: 0,
      description: '',
      city: '',
      dataReturned: false,
    }
  },
  components: {
    AppHeader,
    WeatherPanel,
    SearchBar
  },
  methods: {
    passToPanel(weatherData) {
      this.weatherDataForPanel = weatherData

      this.temperature = weatherData.main.temp

      this.feelsLike = weatherData.main.feels_like

      this.description = weatherData.condition[0].description.charAt(0).toUpperCase() + weatherData.condition[0].description.slice(1)

      this.iconUrl = 'https://openweathermap.org/img/w/' + this.weatherDataForPanel.condition[0].icon + '.png'

      this.city = weatherData.name

      this.dataReturned = true
      // console.log(weatherData)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
