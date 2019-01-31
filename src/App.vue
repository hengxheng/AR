<template>
  <div id="app">
    <SliderBar v-on:changeSlider="changeBrightness" SliderTitle="Brightness" SliderText="Slide to adjust image brightness!" />
    <div>{{ brightness }}</div>
    <SliderBar v-on:changeSlider="changeContrast" SliderTitle="Contrast" SliderText="Slide to adjust image contrast!" />
    <div>{{ contrast }}</div>
  </div>
</template>

<script>
import SliderBar from './components/SliderBar';

export default {
  name: 'app',
  props: {
    brightness: Number,
    contrast: Number
  },
  data: function(){
    return {
      b: this.brightness,
      c: this.contrast
    }
  },
  components: {
    SliderBar
  },
  methods: {
    changeBrightness(b) {
      this.brightness = b;
    },
    changeContrast(c){
      this.contrast = c;
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
