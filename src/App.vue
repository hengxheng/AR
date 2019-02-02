<template>
  <div id="app">
      <AppHeader/>
      <div id="brightness-control">
        <SliderBar @changeSlider="changeBrightness" SliderTitle="Brightness" SliderText="Slide to adjust image brightness!" />
      </div>
      <div id="contrast-control">
        <SliderBar @changeSlider="changeContrast" SliderTitle="Contrast" SliderText="Slide to adjust image contrast!" />
      </div>
      <ImageBoard v-bind:img="i" v-bind:effect="effect" v-bind:brightness="effect.brightness" v-bind:contrast="effect.contrast"/>
      <ImageUploader @imageUploaded="imageUploaded"/>
  </div>
</template>

<script>
  import AppHeader from './components/AppHeader';
  import SliderBar from './components/SliderBar';
  import ImageBoard from './components/ImageBoard';
  import ImageUploader from './components/ImageUploader';

  export default {
    name: 'app',
    data: function(){
      return {
        effect: {
          brightness: 0,
          contrast: 0
        },
        i: this.imgFile,
      }
    },
    components: {
      AppHeader,
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
  $purple: #7144C3;
  $green: #23A15E;
  $blue: #5D83BF;

  body{
    background: #000;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    background: #fcfcfc;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    width: 800px;
    margin:0 auto;
  }
</style>
