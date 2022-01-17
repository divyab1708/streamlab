<template>
  <div id="addSourceContainer">


        <!-- LHS of the screen -->

          <button class="btn btn-primary addSource btn-lg"  data-bs-toggle="modal" data-bs-target="#addSourceModal"><i class="fas fa-plus"></i> Source</button>

          <!-- When no source added -->
          <div class="addSourceDiv" v-if="!videoFeed.show && !screenShare.show"  data-bs-toggle="modal" data-bs-target="#addSourceModal">
            <div>
              <div class="sign"> <i class="fas fa-plus"></i> </div>
              <strong>Add media source</strong>
              <div class="colorGrey">Screenshare, Camera</div>
            </div>
          </div>
          <!-- End - When no source added -->

          <!-- Sources  -->
          <div class="streamSources">

            <div class="row">

              <!--  Contains sources. v-for Loop can be added on one sourceItem to add multiple -->
              <!-- For video feed -->
              <div class=" col-lg-12 col-md-3 col-sm-6 col-xs-6 " v-if="videoFeed.show">
                <div class="sourceItem" :class="{'active' : videoFeed.showOnStream  }">
                  <img :alt="videoFeed.caption" src="@/assets/images/camera.png">
                  <div class="overlay ">
                    <p class="caption">{{videoFeed.caption}}</p>
                    <button class="btn btn-sm" :class="[videoFeed.showOnStream ? 'btn-default' : 'btn-primary']" @click="videoFeed.showOnStream = !videoFeed.showOnStream">{{ videoFeed.showOnStream ? "Hide" : "Show"}} on stream</button>

                  </div>
                </div>
              </div>

              <!-- Screen share -->
              <div class=" col-lg-12 col-md-3 col-sm-6 col-xs-6 " v-if="screenShare.show">
                <div class="sourceItem" :class="{'active' : screenShare.showOnStream  }">
                  <img :alt="screenShare.caption" src="@/assets/images/screenshare.png">
                  <div class="overlay ">
                    <p class="caption">{{screenShare.caption}}</p>
                    <button class="btn btn-sm" :class="[screenShare.showOnStream ? 'btn-default' : 'btn-primary']" @click="screenShare.showOnStream = !screenShare.showOnStream">{{ screenShare.showOnStream ? "Hide" : "Show"}} on stream</button>
                  </div>
                </div>
              </div>
            </div>

          </div>
          <!-- End -  Sources  -->
          

        <!-- End LHS -->
     



    <!-- Modal to add new sources -->
    <div class="modal fade" id="addSourceModal" tabindex="-1" aria-labelledby="addSourceModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered ">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="addSourceModalLabel">Add a new media source</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">

            <!-- Main container for choice -->

            <div class="container-fluid " id="sourceOptions">
              <div class="row">

                <div class="col-lg-6 col-md-6 col-xs-6">
                  <div class="rect align-middle">
                    <div class="rectContent" @click = "addSource('screen')">
                        <strong>Screen Share</strong>
                        <p>Share your entire screen, window or a specific Chrome tab</p>
                    </div>
                  </div>
                </div>

                <div class="col-lg-6 col-md-6 col-xs-6">
                  <div class="rect align-middle" @click = "addSource('video')">
                    <div class="rectContent">
                        <strong>Video Feed</strong>
                        <p>Share a feed of your built-in webcam and microphone. If you do not have a webcam, you can use a "virtual" webcam such as Streamlabs OBS virtual camera</p>
                    </div>
                  </div>
                </div>


              </div>
            </div>

            <!-- End Main container for choice -->

            

          </div>
         
        </div>
      </div>
    </div>
    <!-- End - Modal to add new sources -->


  </div>
</template>

<script>
import {Modal} from 'bootstrap'
export default {
    name: 'AddNewSources',
    props: ["videoFeed", "screenShare"],
    data(){
        return {
           
        }
    
    },
    methods:{
        addSource(sourceType){
            if(sourceType == "screen")
            this.screenShare.show = true
            else
            this.videoFeed.show = true

            var myModalEl = document.querySelector('#addSourceModal')
            var modal = Modal.getInstance(myModalEl)

            modal.hide();
        }
    }
}
</script>

<style lang="scss">
@import '@/assets/scss/colors.scss';

   
  .lhs{
    height: 100vh;
      @media (max-width: 992px) {
            height: auto;
      }

    #addSourceContainer{
      @media (max-width: 992px) {
          margin: 8px 32px;
      }
    }
    // border-right: 2px solid $border;
    background: #12807945;
    .addSource{
      width: 100%;
    }
    .addSourceDiv{
      cursor: pointer;
      margin-top: 8px;
      background: $gray1;
      padding: 16px;
      text-align: center;
    
      &:hover{
          background:$dark-gray1;
      }
      .sign {
          font-size: 30px;
          font-weight: bold;
          color: $primary
      }
      strong{
          font-size: 18px;
      }
      .colorGrey{
          color: $dark-gray;
          font-size: 12px;
      }
    }

    .streamSources{
      position: relative;
      .sourceItem{
          margin-top: 8px;
          position: relative;
          border: 4px solid transparent;
          border-radius: 4px;
          overflow: hidden;

          &.active{
            border: 4px solid $primary;
          }

          img{
            width: 100%;
            border-radius: 4px;
            
          }
   

              
          .overlay {
              height: 100%;
              position: absolute;
              top: 0;
              width: 100%;
              background-color: transparent;
              background-image: linear-gradient(rgba(0,0,0,0), rgba(0,0,0,0.4));
              padding: 8px;
              display:flex;
              justify-content:center;
              align-items:center;
              border-radius: 4px;


              .btn{
                visibility: hidden;
              }

              &:hover .btn{
                visibility: visible;
              }
              .btn-default{
                background: white;
                color: $red;

                &:hover{
                  background: $dark-gray1;
                }

              }
              .caption{
                bottom: 8px;
                left: 8px;
                position: absolute;
                margin: 0;
                color: white;
              }
          }
      }
    }
      
  }

  #addSourceModal{
    .modal-dialog{
        max-width: 50%;
    }
    .rect{
      background: $gray1;
      border-radius: 4px;
      text-align: center;
      height: 200px;
      position: relative;
      display:flex;
      justify-content:center;
      align-items:center;
      cursor: pointer;
      &:hover{
        background: $dark-gray1;
      }
      .rectContent{
        padding: 28px;

      }
      p{
      color: $dark-gray;
      font-size: 12px;
      }
    }
  }

</style>
