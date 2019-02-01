<template>
  <div class="slider-wrapper">
        <div class="slider-header">
            <h2>{{ SliderTitle }}</h2>
        </div>
        <div class="slider-main">
            <input type="range" min="-50" max="50" class="slider" @input="changeSlider"/>
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

</style>
