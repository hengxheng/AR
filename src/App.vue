<template>
  <div id="app">
    <div id="brightness-control">
      <SliderBar v-on:changeSlider="changeBrightness" SliderTitle="Brightness" SliderText="Slide to adjust image brightness!" />
      <div>{{ b }}</div>
    </div>
    <div id="contrast-control">
      <SliderBar v-on:changeSlider="changeContrast" SliderTitle="Contrast" SliderText="Slide to adjust image contrast!" />
      <div>{{ c }}</div>
    </div>
    <ImageBoard v-bind:img="i" />
    <ImageUploader @imageUploaded="imageUploaded"/>
  </div>
</template>

<script>
  import SliderBar from './components/SliderBar';
  import ImageBoard from './components/ImageBoard';
  import ImageUploader from './components/ImageUploader';

  export default {
    name: 'app',
    props: {
      brightness: Number,
      contrast: Number,
      imgFile: Object,
    },
    data: function(){
      return {
        b: this.brightness,
        c: this.contrast,
        i: this.imgFile,
      }
    },
    components: {
      SliderBar,
      ImageBoard,
      ImageUploader
    },
    methods: {
      changeBrightness(b) {
        this.b = b;
      },
      changeContrast(c){
        this.c = c;
      },
      imageUploaded(image){
        this.i = image;
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
