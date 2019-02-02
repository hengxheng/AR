<template>
  <div class="img-uploader-wrapper">
    <div class="container">
      <form enctype="multipart/form-data" novalidate>
        <div class="dropbox">
          <input type="file" @change="onFileChange" accept="image/*" class="input-file">
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
        // handle file changes
        let image = event.target.files[0];
        this.$emit('imageUploaded', image);
      }
    },
  }
</script>

<!-- SASS styling -->
<style lang="scss">

</style>