<template>
  <v-app>
    <v-main>
        <v-img src="@/assets/45.png" style="height:100vh; width:100vw; position: absolute;"></v-img>
        <v-img src="@/assets/46.png" style="height:100vh; width:100vw; position: absolute;"></v-img>
        <!-- <v-img src="@/assets/47.png" style="height:100vh; width:100vw; position: absolute; z-index: 99999999999;"></v-img> -->
        <v-row class="pl-0 pr-0 pt-0 pb-0" >
          <v-col class="pl-0 pr-0 pt-0 pb-0" cols=6 style="background-color: white; height: 100vh"></v-col>
          <v-col class="pl-0 pr-0 pt-0 pb-0"  cols=6 style="background-color: #2B2B2B; height: 100vh"></v-col>
        </v-row>

      <video v-if="!imageData.image" ref="video" class="camera-stream" /> 
      <!-- <div class="box1 blur"></div> -->
      <!-- <div class="box2 blur"></div>
      <div class="box3 blur"></div>
      <div class="box4 blur"></div> -->
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
  width: 40vw;
  height: 40vw;
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
  width: 20vw;
  height: 40vw;
  line-height: 1; 


  position: absolute;
  top: 0;
  bottom: 0;
  left: 20vw;
  right: 0;
  margin: auto;

  z-index: 99999999;
}
/* .box1 {

  border-radius: 0 1000px 1000px 0;
  width: 50vw;
  height: 50vw;
  line-height: 1; 


  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
-webkit-clip-path: polygon(50% 0, 50% 50%, 100% 0, 100% 0);
  clip-path: polygon(50% 0, 50% 50%, 100% 0, 100% 0);
  z-index: 99999999;
} */
/* .box2 {

  border-radius: 0 1000px 1000px 0;
  width: 50vw;
  height: 50vw;
  line-height: 1; 


  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
-webkit-clip-path: polygon(50% 50%, 100% 0, 100% 50%, 100% 50%);
  clip-path: polygon(50% 50%, 100% 0, 100% 50%, 100% 50%);
  z-index: 99999999;
}
.box3 {

  border-radius: 0 1000px 1000px 0;
  width: 50vw;
  height: 50vw;
  line-height: 1; 


  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
-webkit-clip-path: polygon(50% 50%, 100% 100%, 100% 50%);
  clip-path: polygon(50% 50%, 100% 100%, 100% 50%);
  z-index: 99999999;
}
.box4 {

  border-radius: 0 1000px 1000px 0;
  width: 50vw;
  height: 50vw;
  line-height: 1; 


  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  -webkit-clip-path: polygon(50% 50%, 100% 100%, 50% 100%);
  clip-path: polygon(50% 50%, 100% 100%, 50% 100%);
  z-index: 99999999;
} */

.blur {
  backdrop-filter: blur(15px);  
  filter: contrast(120%);
}
.v-application{
  min-height: 100vh;
}


</style>