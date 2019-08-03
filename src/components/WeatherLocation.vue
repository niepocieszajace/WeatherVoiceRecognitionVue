<template>
  <div class="location">
    <div class="location__wraper">
      <h1 class>{{ location }}</h1>
      <span>{{ currentTime }}</span>
    </div>
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
    location: {
      type: String,
      required: true
    },
    sunrise: {
      type: Number,
      required: true
    },
    sunset: {
      type: Number,
      required: true
    }
  },
  data: () => ({
    currentTime: null
  }),
  methods: {
    updateCurrentTime() {
      this.currentTime = new Date().toLocaleTimeString();
    }
  },
  computed: {
    sunriseDate() {
      return new Date(this.sunrise * 1000).toLocaleTimeString();
    },
    sunsetDate() {
      return new Date(this.sunset * 1000).toLocaleTimeString();
    }
  },
  created() {
    this.updateCurrentTime();
    setInterval(() => this.updateCurrentTime(), 1 * 1000);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.location {
  &__wraper {
    margin: 5rem;
  }
}
</style>
