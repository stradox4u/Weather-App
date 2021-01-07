<template>
    <div class="container w-100 row justify-items-start bg-light bg-gradient p-3">
        <h1 class="bg-secondary shadow p-3 text-light rounded my-3">City: {{ city }}</h1>
        <div class="d-flex justify-content-between w-100">
            <img :src="iconUrl" class="rounded float-start col-4" alt="weather condition icon" style="width: 120px">
            <div class="col-8">
                <span class="badge bg-light shadow d-flex justify-content-around">
                    <i class="fas fa-thermometer-half fa-3x text-dark my-auto"></i>
                    <h1 class="p-2 text-dark">{{ temperature }} &deg;C</h1>
                </span>
            </div>
        </div>
        <div class="py-3 mx-auto d-flex justify-content-around"> 
            <h2 class="col-4 my-auto">Feels Like: </h2> 
            <span class="badge bg-light shadow col-8 d-flex justify-content-around">
                <i class="fas fa-feather fa-3x text-dark my-auto"></i>
                <h3 class="p-2 text-dark">{{ feelsLike }} &deg;C</h3>
            </span>
        </div>
        <p class="py-2 h3">{{ description }}</p>
    </div>
</template>

<script>
export default {
    name: 'WeatherPanel',
    data() {
        return {

        }
    },
    props: {
        iconUrl: {
            type: String,
            required: true
        },
        temperature: {
            type: Number,
            required: true
        },
        feelsLike: {
            type: Number,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        city: {
            type: String,
            required: true
        }
    }
}
</script>