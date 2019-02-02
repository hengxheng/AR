<template>
  <div class="slider-wrapper">
        <div class="slider-header">
            <h2>{{ SliderTitle }}</h2>
        </div>
        <div class="slider-main">
            <input type="range" min="-50" max="50" class="slider" value="0" @input="changeSlider"/>
        </div>
        <div class="slider-footer">
            <p>{{ SliderText }}</p>
        </div>
  </div>
</template>

<script>
export default {
    name: 'SliderBar',
    props: {
            SliderTitle: String,
            SliderText: String,
        },
    methods: {
            changeSlider() {
                this.$emit('changeSlider', event.target.value);
            }
        }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .slider-wrapper{
    width: 90%;
    margin: 15px auto;
    background: #fff;
    border-radius: 10x;
    -webkit-box-shadow: 0px 0px 15px -3px rgba(130,130,130,1);
    -moz-box-shadow: 0px 0px 15px -3px rgba(130,130,130,1);
    box-shadow: 0px 0px 15px -3px rgba(130,130,130,1);
 }
</style>
