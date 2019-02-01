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
    }
  },
  watch: {
    img: function(newValue) {
      this.updateCanvasImage(newValue)
    },
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
      var canvas = this.$refs.imageCanvas;
      canvas.width = img.width;
      canvas.height = img.height;

      var ctx = canvas.getContext('2d');
      ctx.drawImage(img,0,0);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>

</style>
