<template>
    <div class="w-100 py-3 mx-auto">
        <form @submit.prevent="submitQuery">
            <div class="input-group col">
                <span class="input-group-text">Enter City Here:</span>
                <input type="text" class="form-control" placeholder="City Name" v-model="queryCity">
            </div>
            <div class="d-grid gap-2 py-3">
                <base-button class="shadow">Submit</base-button>
            </div>
        </form>
    </div>
</template>

<script>
import BaseButton from './BaseButton.vue'
import axios from 'axios'

export default {
    name: 'SearchBar',
    components: {
        BaseButton,
    },
    data() {
        return {
            queryCity: '',
            openWeatherKey: 'cd495a3382f45fd682aa7792340dd251',
            openWeatherUrl: 'https://api.openweathermap.org/data/2.5/weather?q=',
            weatherData: {},
        }
    },
    emits: ['data-returned'],
    methods: {
        submitQuery() {
            axios.get(this.openWeatherUrl + this.queryCity + '&units=metric' + '&appid=' + this.openWeatherKey)
            .then(response => {
                this.weatherData.main = response.data.main
                this.weatherData.condition = response.data.weather
                this.weatherData.name = response.data.name

                this.$emit('data-returned', this.weatherData)
                // console.log(response.data.name)
            })
        }
    }
}
</script>