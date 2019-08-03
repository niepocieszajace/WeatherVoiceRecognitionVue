<template>
  <div class="Weather">
    <WeatherLocation
      v-if="!!apiResponse"
      :location="apiResponse.name"
      :sunrise="apiResponse.sys.sunrise"
      :sunset="apiResponse.sys.sunset"
    />
    <WeatherTemperature
      v-if="!!apiResponse"
      :temperature="apiResponse.main.temp"
      :description="apiResponse.weather[0].main"
    />
  </div>
</template>

<script>
import axios from "axios";

import WeatherLocation from "./WeatherLocation";
import WeatherTemperature from "./WeatherTemperature";

export default {
  name: "Weather",
  components: {
    WeatherTemperature,
    WeatherLocation
  },
  props: {
    location: {
      type: String,
      required: true
    }
  },
  data: () => ({
    apiResponse: ""
  }),
  methods: {
    getWeather() {
      axios
        .get(
          "http://api.openweathermap.org/data/2.5/weather?q=Kraków&APPID=ecc7afea1aa9eb30728dd04dbf88fcb0&units=metric"
        )
        .then(res => (this.apiResponse = res.data))
        .catch(err => console.log(err));
    }
  },
  created() {
    this.getWeather();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.Weather {
  height: 100%;
  align-items: center;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
</style>