<template>
  <div id="streamContainer">
    <div class="streamContainer">
        <div class="streamMain " :class="streamLayout">

            <!-- displays screenshare -->
            <div class="screenShareContainer"><img class="screenShare" :alt="screenShare.caption" v-if="screenShare.showOnStream"  src="@/assets/images/screenshare.png"></div>

            <!-- displays video stream -->
            <div class="videoFeedContainer"><img class="videoFeed" :alt="videoFeed.caption" v-if="videoFeed.showOnStream" src="@/assets/images/camera.png" /></div>

            

        </div>
        <div class="layoutOptions" >
            <div class="onlyVideoFeed" v-if="videoFeed.showOnStream && !screenShare.showOnStream ">
                <button class="btn btn-default " :class="{'active': streamLayout == 'videoFeed100'}" @click="streamLayout='videoFeed100'"><div class="vf100Icon layoutIcon"></div></button>
                <button class="btn btn-default" :class="{'active': streamLayout == 'videoFeed80'}" @click="streamLayout='videoFeed80'"><div class="vf80Icon layoutIcon"></div></button>
                <button class="btn btn-default" :class="{'active': streamLayout == 'videoFeed60'}" @click="streamLayout='videoFeed60'"><div class="vf60Icon layoutIcon"></div></button>
            </div>
            <div class="bothSource" v-if="videoFeed.showOnStream && screenShare.showOnStream ">
                <button class="btn btn-default" :class="{'active': streamLayout == 'videoFeedRight'}" @click="streamLayout='videoFeedRight'"><div class="vfssRightIcon layoutIcon"></div></button>
                <button class="btn btn-default" :class="{'active': streamLayout == 'videoFeedLeft'}" @click="streamLayout='videoFeedLeft'"><div class="vfssLefttIcon layoutIcon"></div></button>
                <button class="btn btn-default" :class="{'active': streamLayout == 'videoFeedSplit'}" @click="streamLayout='videoFeedSplit'"><div class="vfssSplitIcon layoutIcon"></div></button>
            </div>
        </div>
    </div>

  </div>
</template>

<script>
import '@/assets/fontawesome/css/all.min.css';

export default {
    name: 'StreamContainer',
    props: ["videoFeed", "screenShare"],
    watch:{
        videoFeed: {
            handler(){  
                this.setDefault()
            },
            deep: true,
            immediate: true 

        },
        screenShare: {
            handler(){  
                this.setDefault()
            },
            deep: true,
            immediate: true 

        }
    },

    data(){
        return {
            streamLayout: ""
    
        }
    
     },
    methods:{
        setDefault(){
            if(this.videoFeed.showOnStream && !this.screenShare.showOnStream){
                this.streamLayout = "videoFeed100"
            }
            else if(!this.videoFeed.showOnStream && this.screenShare.showOnStream){
                this.streamLayout = ""
            }else if(this.videoFeed.showOnStream && this.screenShare.showOnStream){
                this.streamLayout = "videoFeedRight"
            }
        }
    }
}
</script>

<style lang="scss">
@import '@/assets/scss/colors.scss';

.layoutIcon{
    width: 50px;
    height: 30px;
    background-repeat: no-repeat;
    margin: auto;
    background-size: 100%;

    &.vf100Icon,&.vf80Icon,&.vf60Icon{
        background-image: url('images/videofeedLayoutIcon.png');
        background-position: 50%;
    }

    &.vf80Icon{
        background-size: 80%;
    }
    &.vf60Icon{
        background-size: 60%;
    }

    &.vfssRightIcon{
        background-image: url('images/vfssRight.png');
    }
    &.vfssLefttIcon{
        background-image: url('images/vfssLeft.png');
    }
    &.vfssSplitIcon{
        background-image: url('images/vfssSplit.png');
    }
}


// .fa,.fas,.far,.fal,.fab {
//   font-family: "Font Awesome 5 Free";
// }
  #streamContainer{
      
  }
  .streamContainer {
    // margin: auto;

    margin: 8px 32px;
    display:flex;
    flex-direction: column;
    justify-content:center;
    align-items:center;
    height: 90vh;
    @media (max-width: 1050px) {
        height: auto;
        display: block;
    }   
    .streamMain {
        background: $primary-darkest;
        aspect-ratio: 16/9;
        width: 90%;
        position: relative;
        @media (max-width: 1050px) {
            width: 100%;
        }   
      
    }
    .layoutOptions{
        min-height: 35px;
        text-align: center;
        margin: 8px;
        background: $gray1;
        .btn{
            min-width: 80px;
            border: 2px solid transparent;
            border-radius: 4px;
           padding: 4px;
            &.active{
                border-color: $red;
            }
        }
    }
    .screenShare{
        width: 100%;
    }
    .videoFeed100{
        .videoFeed{
            width: 100%;

        }
    }
    .videoFeed80{
        .videoFeed{
            width: 80%;
        }
    }
    .videoFeed60{
        .videoFeed{
            width: 60%;
        }
    }
    .videoFeed80,.videoFeed60{
        .videoFeed{
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);

        }
    }
    .videoFeedRight,.videoFeedLeft{
        .videoFeed{
            position: absolute;
            width: 25%;
            bottom: 16px;
        }
    }
    .videoFeedRight{
        .videoFeed{
            right: 16px;
        }
    }
    .videoFeedLeft{
        .videoFeed{
            left: 16px;
        }
    }

    .videoFeedSplit{
        &.streamMain{
            display: flex;
            justify-content:center;
    align-items:center;
        }
        .videoFeedContainer{
            height: 80%;
            max-height: 80%;
            display: inline-block;
            overflow: hidden;
            position: relative;
            width: 33%;
        }
        .videoFeed{
            // width: 100%;
            transform: translateX(-25%);
            height: 100%;

        }
        .screenShareContainer{
            width: 66%;
            margin-right: 1%;
            display: inline-block;
            height: 80%;

        }
        .screenShare{
            width: 100%;
            height: 100%;
            // margin-top: 50%;
            // transform: translateY(-50%);

        }
       
    }
    
  }


</style>
