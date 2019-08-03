<template>
  <div>
    <button :disabled="error" @click="recognize">Talk</button>
  </div>
</template>

<script>
export default {
  name: "VoiceRecognition",
  data: () => ({
    error: false,
    recognition: null,
    location: ""
  }),
  methods: {
    createSpeechRecognition() {
      const SpeechRecognition =
        window.SpeachRecognition || window.webkitSpeechRecognition;

      if (!SpeechRecognition) {
        this.error = true;
        throw new Error(
          "Speech Recognition does not exist on this browser. Use Chrome or Firefox"
        );
      }

      this.recognition = new SpeechRecognition();
    },
    recognize() {
      const that = this;
      this.recognition.start();

      this.recognition.onresult = e => {
        const current = e.resultIndex;
        const transcript = e.results[current][0].transcript;

        console.log(e);

        this.location = transcript;
      };

      this.recognition.onend = () => {
        this.$emit("onRecognitionEnd", {
          location: this.location
        });
      };
    }
  },
  created() {
    this.createSpeechRecognition();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
