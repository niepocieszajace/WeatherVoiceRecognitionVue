<template>
  <div class="WeatherTemperature">
    <div class="WeatherTemperature__degree">
      <h2 class="WeatherTemperature__degree-temp">{{ temperature }}</h2>
      <span>&deg;C</span>
    </div>

    <div class="WeatherTemperature-descript">{{ description }}</div>
  </div>
</template>

<script>
export default {
  name: "WeatherTemperature",
  props: {
    temperature: {
      type: Number,
      required: true
    },
    description: {
      type: String,
      required: true
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.WeatherTemperature {
  &__degree {
    display: flex;
  }
}
</style>
