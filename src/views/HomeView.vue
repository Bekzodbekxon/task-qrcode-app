<template>
  <div class="home">

   <div class="box">
     <div class="textarea__box">
       <textarea class="textarea" v-model="value" placeholder="Enter text..."></textarea>
     </div>

     <div>
       <qrcode-vue :value="value" id="canvas" :size="size" level="H"></qrcode-vue>
     </div>
   </div>
<!--    <img alt="Vue logo" src="../assets/logo.png">-->
    <div class="">
      <button class="button" @click="downloadPng">Download</button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import QrcodeVue from 'qrcode.vue'

export default {
  name: 'HomeView',
  components: {
    QrcodeVue
  },
  data(){
    return {
      value: 'task-qrcode',
      size: 300,
    }
  },
  methods:{
    downloadPng(){
      var canvas = document.getElementById("canvas");
// Convert the canvas to data
      var image = canvas.toDataURL();
// Create a link
      var aDownloadLink = document.createElement('a');
// Add the name of the file to the link
      aDownloadLink.download = 'canvas_image.png';
// Attach the data to the link
      aDownloadLink.href = image;
// Get the code to click the download link
      aDownloadLink.click();
    }
  }
}
</script>
<style>
.button {
  margin-top: 20px;
}
.textarea {
  min-width: 200px;
  min-height: 150px;
}
.box {
  display: flex;
  justify-content: center;
  align-items: center;
}
.textarea__box {
  margin-right: 10px;
}
</style>
