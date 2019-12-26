<template>
  <div class="main">
    <div class="cropper-area"> 
      <vue-cropper
        :aspect-ratio="16 / 9"
        ref="cropper"
        :src="imgSrc"
        alt="Source Image"
        preview=".preview"
        :cropmove="imageInfo"
      >
      </vue-cropper>
      <button @click="cropImage" type="button">
        Crop
      </button>
    </div>
    <div class="cropped-area">
      <img
        v-if="cropImg" 
        :src="cropImg"
        class="cropped-img"
        alt="Cropped Image" 
      />
    </div>
  </div>
</template>

<script>
import VueCropper from 'vue-cropperjs';
import 'cropperjs/dist/cropper.css';

export default {
  components: { VueCropper },
  name: 'HelloWorld',
  data(){
    return {
      cropImg: '',
      imgSrc: "https://images.unsplash.com/photo-1499084732479-de2c02d45fcc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3289&q=80"
    }
  },
  methods: {
    imageInfo(){

    },
    cropImage(){
      this.cropImg = this.$refs.cropper.getCroppedCanvas().toDataURL();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  padding: 10px 20px;
  background: aquamarine;
  border: none;
  border-radius: 5px;
}
  .main {
    display: flex;

  }

  .cropper-area {
    flex: 1;
  }

  .cropped-area {
    flex: 1;
  }
  .cropped-img {
    width: 100%;
  }
</style>
