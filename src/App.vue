<template>
  <div id="app">
    <VoiceRecognition @onRecognitionEnd="handleLocationChange"></VoiceRecognition>
    <Weather :location="location"></Weather>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Weather from "./components/Weather.vue";
import VoiceRecognition from "./components/VoiceRecognition.vue";

export default {
  name: "app",
  components: {
    VoiceRecognition,
    Weather
  },
  data: () => ({
    location: ""
  }),
  methods: {
    handleLocationChange(e) {
      this.location = e.location;
    }
  }
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  align-items: center;

  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
  background-image: linear-gradient(to top, #4481eb 0%, #04befe 100%);
}
</style>
