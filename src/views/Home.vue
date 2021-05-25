<template>
  <div class="home">
    <div v-if="error">{{ error }}</div>
    <div v-if="weather">
      <h1>{{ weather.current.weather[0].description }}</h1>
      <div>
        
      </div>
      <div>
        <TemperatureChart :hourly="weather.hourly" />
        <!-- <MonthlyChart /> -->
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import TemperatureChart from "@/components/TemperatureChart";

export default {
  name: "Home",
  components: {
    TemperatureChart,
  },
  data() {
    return {
      weather: null,
      error: null,
    };
  },
  created() {
    const apiKey = process.env.VUE_APP_WEATHER_API_KEY;
    let lat = 48.210033;
    let lon = 16.363449;
    let apiUrl = `https://api.openweathermap.org/data/2.5/onecall?appid=${apiKey}&lat=${lat}&lon=${lon}&units=metric&lang=de`;

    axios
      .get(apiUrl)
      .then((response) => {
        this.weather = response.data;
        console.log(this.weather);
      })
      .catch((e) => {
        this.error = e.message;
      });
  },
  computed: {
    iconUrl() {},
  },
};
</script>
