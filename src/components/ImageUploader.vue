<!-- HTML Template -->
<!-- https://www.academind.com/learn/vue-js/snippets/image-upload/ -->
<template>
  <div class="img-uploader-wrapper">
    <div class="container">
      <form enctype="multipart/form-data" novalidate>
        <div class="dropbox">
          <input type="file" :name="uploadFieldName" :disabled="isSaving" @change="onFileChange" accept="image/*" class="input-file">
        </div>
      </form>
    </div>
  </div>
</template>

<!-- Javascript -->
<script>
  const STATUS_INITIAL = 0, STATUS_SAVING = 1, STATUS_SUCCESS = 2, STATUS_FAILED = 3;

  export default {
    name: 'ImageUploader',
    data: function() {
      return {
        uploadedImage: null,
        uploadError: null,
        currentStatus: null,
        uploadFieldName: 'photos'
      }
    },
    computed: {
      isInitial() {
        return this.currentStatus === STATUS_INITIAL;
      },
      isSaving() {
        return this.currentStatus === STATUS_SAVING;
      },
      isSuccess() {
        return this.currentStatus === STATUS_SUCCESS;
      },
      isFailed() {
        return this.currentStatus === STATUS_FAILED;
      }
    },
    methods: {
      reset() {
        // reset form to initial state
        this.currentStatus = STATUS_INITIAL;
        this.uploadedFiles = [];
        this.uploadError = null;
      },
      // save(formData) {
      //   // upload data to the server
      //   this.currentStatus = STATUS_SAVING;
      // },
      onFileChange(event) {
        // handle file changes
        let image = event.target.files[0];
        this.$emit('imageUploaded', image);
      }
    },
    mounted() {
      this.reset();
    },
  }
</script>

<!-- SASS styling -->
<style lang="scss">

</style>