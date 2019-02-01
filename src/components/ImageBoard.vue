<template>
  <div class="image-board-wrapper">
    <canvas id="imageCanvas" ref="imageCanvas"></canvas>
  </div>
</template>

<script>
export default {
  name: 'ImageBoard',
  props: {
    img: File
  },
  data: function(){
    return{
      // img: this.image,
      window: {
        width: 0,
        height: 0
      }
    }
  },
  created: function(){
    this.window.width = window.innerWidth;
    this.window.height = window.innerHeight;
  },
  watch: {
    img: function(newValue) {
      this.updateCanvasImage(newValue)
    }
  },
  methods:{
    updateCanvasImage(img) {
      var self = this;
      var reader = new FileReader();
      reader.onload = () => {
          var imgObj = new Image();
          imgObj.onload = function() {
              self.drawCanvasImage(imgObj);
          }
          imgObj.src = URL.createObjectURL(img);
      };
      reader.readAsDataURL(img);
    },
    drawCanvasImage(img) {
      let canvas = this.$refs.imageCanvas;
      let imageRatio = img.height/img.width;
      canvas.width = this.window.width
      canvas.height = this.window.width * imageRatio;
      let ctx = canvas.getContext('2d');
      ctx.drawImage(img,0,0,canvas.width,canvas.height);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  #imageCanvas {
    width: 100%;
  }
</style>
