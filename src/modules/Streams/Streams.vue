<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row stream">
        <!-- LHS of the screen -->
        <div class="col-lg-2 col-md-12 lhs">
          <add-source :videoFeed="videoFeed" :screenShare="screenShare" />
        </div>
        <!-- End LHS -->
        <!-- RHS of the screen ie STREAM -->
        <div class="col-lg-10 col-md-12 background">
          <show-stream :videoFeed="videoFeed" :screenShare="screenShare" />
          
        </div>
        <!-- End RHS of the screen ie STREAM -->

      </div>

    </div>
    <div class="footerButtons text-center">
      <div>
        <button class="btn btn-default"><i class="fas fa-comment"></i>Chat</button>
        <button class="btn btn-default"><i class="far fa-dot-circle"></i> Record</button>
        <button class="btn btn-primary"><i class="fas fa-rocket"></i>Go Live</button>
      </div>
    </div>

   

  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css"

import AddSource from "./addNewSources.Streams.vue"
import showStream from "./showStream.Streams.vue"
export default {
  name: 'Streams',
  components:{
    "add-source": AddSource,
    "show-stream": showStream
  },
  data(){
    return {
      videoFeed:{
        img: "@assets/images/camera.png",
        caption: "My video feed",
        show: false,
        showOnStream: false
      },
      screenShare:{
        img: "@assets/images/screenshare.png",
        caption: "My screen feed",
        show: false,
        showOnStream: false

      }
    }
    
  },
  methods:{
  
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/colors.scss';
@import '@/assets/scss/common.scss';




// CSS specific to this page
.stream{
  >div{
    padding-top: 16px;
    padding-bottom: 16px;
  }
}
  


  .footerButtons{
    background: transparent;
    position: fixed;
    width: 100%;
    left: 0;
    bottom: 0;
    .btn{
      font-weight: bold;

    }
    > div{
      display: inline-block;
      margin: auto;
      border: 2px solid $border;
      padding: 8px;
      border-radius: 4px;
      background: white;
    }
  }
  .background{
    // background-image: url('images/background.png');
      // background-size: 100%;
  }
  


</style>
