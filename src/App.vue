<template>
  <v-app>
    <v-main>

        <v-row class="pl-0 pr-0 pt-0 pb-0" >
          <v-col class="pl-0 pr-0 pt-0 pb-0" cols=6 style="background-color: white; height: 100vh"></v-col>
          <v-col class="pl-0 pr-0 pt-0 pb-0"  cols=6 style="background-color: black; height: 100vh"></v-col>
        </v-row>

      <video v-if="!imageData.image" ref="video" class="camera-stream" /> 
      <div class="box blur"></div>
    </v-main>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  data() {
        return {
            mediaStream: null,
            imageData: {
                image: '',
                image_orientation: 0,
            },
        }
    },
    mounted() {
        navigator.mediaDevices.getUserMedia({video: true})
            .then(mediaStream => {
                    this.$refs.video.srcObject = mediaStream;
                    this.$refs.video.play()
                    this.mediaStream = mediaStream                   
            })   
    },
}
</script>
<style>
.camera-stream {
  object-fit: cover;
  width: 50vw;
  height: 50vw;
  border-radius: 100%;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  -moz-transform: scale(-1, 1); 
  -webkit-transform: scale(-1, 1); 
  -o-transform: scale(-1, 1); 
  transform: scale(-1, 1); 
  filter: FlipH;

  filter: grayscale(1);
  -webkit-filter: grayscale(1); 
  filter: grayscale(100%); 
}

.box {

  border-radius: 0 1000px 1000px 0;
  width: 25vw;
  height: 50vw;
  line-height: 1; 


  position: absolute;
  top: 0;
  bottom: 0;
  left: 25vw;
  right: 0;
  margin: auto;


  z-index: 99999999;
  

}
.blur {
  backdrop-filter: blur(15px);  
}
</style>