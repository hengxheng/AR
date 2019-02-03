<template>
  <div id="app">
      <AppHeader/>
      <div id="brightness-control">
        <SliderBar @changeSlider="changeBrightness" SliderTitle="Brightness" SliderText="Slide to adjust image brightness!" />
      </div>
      <div id="contrast-control">
        <SliderBar @changeSlider="changeContrast" SliderTitle="Contrast" SliderText="Slide to adjust image contrast!" />
      </div>
      <div class="image-block">
          <div class="image-block-inner">
            <ImageBoard :img="i" :brightness="effect.brightness" :contrast="effect.contrast"/>
            <ImageUploader @imageUploaded="imageUploaded"/>
          </div>
      </div>
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
  $inner-width: 90%;
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
    width: 650px;
    margin:25px auto;
    padding-bottom: 30px;
  }

  #brightness-control{
    .slider-header{
      h2{
        color:$green;
      }
    }
    input[type=range]{
      &::-webkit-slider-thumb {
          background: $green;
      }
      &::-webkit-slider-runnable-track {
        background: $green;
      }

      &:focus::-webkit-slider-runnable-track {
        background: $green;
      }
    }
  }

  #contrast-control{
    .slider-header{
      h2{
        color:$blue;
      }
    }
    input[type=range]{
      &::-webkit-slider-thumb {
          background: $blue;
      }
      &::-webkit-slider-runnable-track {
        background: $blue;
      }

      &:focus::-webkit-slider-runnable-track {
        background: $green;
      }
    }
  }
  
  .image-block{
    width: $inner-width;
    margin:30px auto 15px;
    border-radius: 5px;
  }
</style>
