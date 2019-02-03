<template>
  <div class="image-board-wrapper">
    <div id="canvasContainer" ref="canvasContainer">
      <canvas id="imageCanvas" ref="imageCanvas"></canvas>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ImageBoard',
  props: {
    img: File,
    brightness: Number,
    contrast: Number
  },
  data: function(){
    return{
      imgData: {},
      myCanvas: {},
      myCTX: {},
    }
  },
  watch: {
    img: function(img) {
      this.updateCanvasImage(img);
    },
    brightness: function(b1, b2){
      this.adjustBrightness(b1-b2);
    },
    contrast: function(c1, c2){
      this.adjustContrast(c1-c2);
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
      let ctx = canvas.getContext('2d');
      let imageRatio = img.height/img.width;
      canvas.width = this.$refs.canvasContainer.offsetWidth;
      canvas.height = canvas.width * imageRatio;
      ctx.drawImage(img,0,0,canvas.width,canvas.height);
    },

    adjustBrightness(brightness){
      let canvas = this.$refs.imageCanvas;
      let ctx = canvas.getContext('2d');
      let imgData = ctx.getImageData(0,0,canvas.width,canvas.height);

      var d = imgData.data;
      for (var i=0; i<d.length; i+=4) {
        d[i] += brightness;
        d[i+1] += brightness;
        d[i+2] += brightness;
      }
      ctx.putImageData(imgData, 0, 0);
    },

    adjustContrast(contrast){
      let canvas = this.$refs.imageCanvas;
      let ctx = canvas.getContext('2d');
      let imgData = ctx.getImageData(0,0,canvas.width,canvas.height);

      var d = imgData.data;
      contrast = (contrast/100) + 1;  //convert to decimal & shift range: [0..2]
      var intercept = 128 * (1 - contrast);
      for(var i=0;i<d.length;i+=4){   //r,g,b,a
          d[i] = d[i]*contrast + intercept;
          d[i+1] = d[i+1]*contrast + intercept;
          d[i+2] = d[i+2]*contrast + intercept;
      }
      ctx.putImageData(imgData, 0, 0);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  #imageCanvas {
    width: 100%;
    display: block;
    background: #a2a2a2;
    border-top-right-radius: 10px;
    border-top-left-radius: 10px;
  }
</style>
