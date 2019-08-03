<template>
  <div class="location">
    <div class="location__wraper">
      <h3>Sunrise</h3>
      <span>{{ sunriseDate }}</span>
      <h3>Sunset</h3>
      <span>{{ sunsetDate }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "WeatherLocation",
  props: {
    sunrise: {
      type: Number,
      required: true
    },
    sunset: {
      type: Number,
      required: true
    }
  },
  computed: {
    sunriseDate() {
      return new Date(this.sunrise * 1000).toLocaleTimeString();
    },
    sunsetDate() {
      return new Date(this.sunset * 1000).toLocaleTimeString();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
