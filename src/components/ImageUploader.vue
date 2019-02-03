<template>
  <div class="img-uploader-wrapper">
    <div class="container">
      <form enctype="multipart/form-data" novalidate>
        <div class="input-row">
          <div class="input-col">
            <label for="filename" class="input-label">
              NAME
            </label>
            <input type="text" id="filename" name="filename" placeholder="A LONG FILE NAME ..."/>
          </div>
          <div class="input-col">
            <input type="file" id="thefile" name="thefile" @change="onFileChange" accept="image/*" class="input-file">
            <label for="thefile" class="FileUploader"><i></i>  UPLOAD</label>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'ImageUploader',
    methods: {
      onFileChange(event) {
        let image = event.target.files[0];
        this.$emit('imageUploaded', image);
      }
    },
  }
</script>

<style lang="scss">
  $blue: #5D83BF;
  $green: #23A15E;
  .img-uploader-wrapper{
    border: 1.5px solid #dadada;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    box-sizing: border-box;
    padding: 25px 15px 15px;
    .input-row{
      display:flex;
      box-sizing: border-box;
      padding: 5px;
      margin: 5px auto;
      justify-content: space-between;
      .input-col{
        display:flex;
        justify-content: flex-start;
        .input-label{
          display:inline-block;
          background: #f0f0f0;
          color: #a2a2a2;
          height: 40px;
          text-align: center;
          padding: 10px;
          box-sizing: border-box;
          font-size: 16px;
          font-weight: bold;
          line-height: 22px;
          letter-spacing: 2px;
          border-top-left-radius: 5px;
          border-bottom-left-radius: 5px;
          border: 1.5px solid #dadada;
        }
        input[type=text]{
          display:inline-block;
          background: transparent;
          color: $green;
          height: 40px;
          font-size: 16px;
          line-height: 22px;
          border-top-right-radius: 5px;
          border-bottom-right-radius: 5px;
          padding: 6px 10px 0;
          box-sizing: border-box;
          border: 1.5px solid #dadada;
          &::placeholder{
            font-size: 18px;
            font-weight: bold;
            color: $green;
          }
        }
      }
    }
  }

  .FileUploader{
    background: #f0f0f0;
    color: $blue;
    height: 40px;
    text-align: center;
    padding: 10px;
    box-sizing: border-box;
    display:inline-block;
    font-weight: bold;
    font-size: 16px;
    line-height: 22px;
    border-radius: 5px;
    border: 1.5px solid #dadada;
    cursor: pointer;
    &:hover{
      background:#dadada;
    }
    i{
      color: $blue;
      display:inline-block;
      &::after{
        content:'';
        margin-right: 5px;
        display:inline-block;
        width: 0;
        height: 0;
        border-style: solid;
        border-width: 0 7.5px 13px 7.5px;
        border-color: transparent transparent $blue transparent;
      }
    }
  }
  input[type=file]{
    width: 0.1px;
    height: 0.1px;
    opacity: 0;
    overflow: hidden;
    position: absolute;
    z-index: -1;
  }
</style>