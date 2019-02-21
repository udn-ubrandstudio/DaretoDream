<template>
  <div class="videoBox">
    <youtube :src="videoInfo.video"></youtube>
    <div class="content"  :style="{'background-image': 'url(' + srcRWD(videoInfo.img, videoInfo.img_web) + ')' }" >
      <a :href="videoInfo.linkTo">
        <div>
          <h5 class="name"> {{ videoInfo.name }} </h5>
          <h5 class="slogan"><div v-html="videoInfo.slogan"></div></h5>
          <div class="more">點看內文<img class="moreArrow" :src="srcRWD(more, moreWeb)" alt=""></div>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
import youtube from '@/components/base/Youtube.vue'
import srcRWD from '@/mixin/srcRWD.js'

export default {
  name: 'videoBox',
  mixins: [srcRWD],
  data () {
    return {
      more: require('@/../static/more.svg'),
      moreWeb: require('@/../static/more_web.svg')
    }
  },
  props: {
    videoInfo: Object
  },
  components: {
    youtube
  },
}
</script>

<style lang="scss" scoped>
.videoBox{
  margin-top: 25px;
  @media screen and (min-width: 768px) and (max-width: 1023px) {
    margin-top: 50px;
  }
  @media screen and (min-width: 1024px) {
    margin-top: 50px;
  }
  .content {
      position: relative;
      display: -webkit-flex;
      display: flex;
      -webkit-align-items: center;
      align-items: center;
      -webkit-justify-content: center;
      justify-content: center;
      // background-position: center;
      background-repeat: no-repeat;
      background-size: cover;
      @media screen and (min-width: 768px) and (max-width: 1023px) {
            height: 150px;
          }
      a {
           width: 100%;
           height: 100%;
           text-decoration: none;
           color: black;
           font-weight: bolder;
      .name {
          text-align: center;
          font-size: 21px;
          margin-bottom: 0px;
          line-height: 1;
          @media screen and (min-width: 768px) and (max-width: 1023px) {
            font-size: 34px;
             margin-top: 30px;
             margin: 5px;
          }
          @media screen and (min-width: 1024px) {
            font-size: 40px;
             margin-top: 30px;
          }
      }
      .slogan {
          @media screen and (min-width: 768px) and (max-width: 1023px) {
            font-size: 32px;
          }
          @media screen and (min-width: 1024px) {
            font-size: 56px;
          }
          margin-bottom: 30px;
          padding: 0;
          line-height: 1.5;
          font-family: 微軟正黑體;
          font-weight: bold;
          letter-spacing: -0.6px;
          font-size: 21px;
          text-align: center;
       }     
      .more {        
        position: absolute;
        right: 0;
        bottom: 0;
        font-size: 16px;
        font-weight: bolder;
        display: flex;
        align-items: center;
        vertical-align: -webkit-baseline-middle;
        color: #e60414;  
        @media screen and (min-width: 768px) and (max-width: 1023px) {
          font-size: 24px;
        }
        @media screen and (min-width: 1024px) {
          font-size: 24px;
        }
        .moreArrow {
          width: 18px;
          margin: 0 2px;
          @media screen and (min-width: 768px) and (max-width: 1023px) {
            font-size: 20px;
          }
          @media screen and (min-width: 1024px) {
            font-size: 20px;
          }
        }
      }
    }
  }
}
</style>
