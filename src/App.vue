<template>
  <div id="app">
    <div id="brightness-control">
      <SliderBar v-on:changeSlider="changeBrightness" SliderTitle="Brightness" SliderText="Slide to adjust image brightness!" />
    </div>
    <div id="contrast-control">
      <SliderBar v-on:changeSlider="changeContrast" SliderTitle="Contrast" SliderText="Slide to adjust image contrast!" />
    </div>
    <ImageBoard v-bind:img="i" v-bind:effect="effect" v-bind:brightness="effect.brightness" v-bind:contrast="effect.contrast"/>
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
      brightness: {
        defualt: 0,
        type: Number,
      },
      imgFile: Object,
    },
    data: function(){
      return {
        effect: {
          brightness: 25,
          contrast: 25
        },
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
        this.effect.brightness = parseInt(b);
      },
      changeContrast(c){
        this.effect.contrast = parseInt(c);
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
    width: 800px;
    margin:0 auto;
  }
</style>
