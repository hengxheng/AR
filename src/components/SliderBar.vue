<template>
  <div class="slider-wrapper">
        <div class="slider-header">
            <h2>{{ SliderTitle }}</h2>
        </div>
        <div class="slider-main">
            <input type="range" min="-50" max="50" class="adjust-range" value="0" @input="changeSlider"/>
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

<style lang="scss" scoped>  
    .slider-wrapper{
        width: 90%;
        margin: 15px auto;
        background: #fff;
        border-radius: 10px;
        box-sizing: border-box;
        padding: 15px;
        box-shadow: 0px 0px 15px -3px rgba(130,130,130,1); 
    }
    input[type=range]{
        width: 100%;
        -webkit-appearance: none;
        appearance: none;
        &::-webkit-slider-thumb {
            -webkit-appearance: none;
            border: 3px solid #fff;
            height: 25px;
            width: 25px;
            border-radius: 50%;
            background: #111;
            cursor: pointer;
            margin-top: -7px; /* You need to specify a margin in Chrome, but in Firefox and IE it is automatic */
            box-shadow: 0px 0px 15px -3px rgba(130,130,130,1); 
        }

        &::-moz-range-thumb {
            box-shadow: 0px 0px 15px -3px rgba(130,130,130,1); 
            border: 3px solid #fff;
            height: 25px;
            width: 25px;
            border-radius: 50%;
            background: #111;
            cursor: pointer;
        }

        &::-ms-thumb {
            box-shadow: 0px 0px 15px -3px rgba(130,130,130,1); 
            border: 1px solid #000000;
            height: 25px;
            width: 25px;
            border-radius: 3px;
            background: #ffffff;
            cursor: pointer;
        }

        &::-webkit-slider-runnable-track {
            width: 100%;
            height: 10px;
            cursor: pointer;
            box-shadow: 0px 0px 15px -3px rgba(130,130,130,1); 
            background: #000;
            border-radius: 3px;
            border: 0.2px solid #010101;
        }

        &:focus::-webkit-slider-runnable-track {
            background: #f1f1f1;
        }
    }

</style>
