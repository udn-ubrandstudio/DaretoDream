<template>
  <div id="app">
    <indicator></indicator>
    <div class="cover" :style="{'background-image': 'url(' + srcRWD(cover, coverWeb) + ')' }">
      <!-- <img :src="srcRWD(cover, coverWeb)" alt="" class="main-cover"> -->
      <img :src="coverTitle" alt="" class="cover-title">
      <img :src="logo" alt="" class="logo">
    </div>
    <content-container>
      <br>
      <share href="https://udn.com/upf/ubrand/2019_data/DaretoDream/index.html"></share>
      <br>
      <div class="title-track-same-month">
         <youtube src="https://www.youtube.com/embed/GwF4fFnxTkg"></youtube>
        <div class="content">
          <a :href="hotVideo">
            <div class="content-item new">
              NEW
            </div>
            <div class="content-item slogan">
              <h3>Duncan: 有生之年<br>要畫出一幅讓世界看見的作品</h3>
            </div>
          </a>
        </div>
      </div>
      <br>
      <br>
      <p>Dare to Dream意味勇敢追夢，超人氣圖文創作者Duncan曾說過「夢想再高，你還是碰得到！」聯合報採訪6位夢想人物故事，從圖文創作家、饒舌歌手、街頭小提琴手到滑輪新星等，每月帶你看一篇逐夢故事，不管你的夢想多小，只要敢做夢，都有實現的可能！</p>
      <br>
      <br>
      </content-container>
      <content-container style="background-image: linear-gradient(to bottom, #f2f2f2, rgba(255, 255, 255, 0));">
      <div class="anchor-web">
        <h3 class="anchor-web-title">夢想人物系列　影音故事</h3>
        <ul>
          <li v-for="item in profiles" :id="item.id" :key="item.id" @click.prevent="handle_scrollTo(item.title, item.idTo, item.isLock, item.id)" :class="{ shake: item.isLock }">
            <img :src="item.profile_web" alt="">
            <div class="describe">
                <p>{{ item.title }}</p>
                <p>{{ item.name }}</p>
              </div>
          </li>
        </ul>
      </div>
      </content-container>

        <div class="anchor-mobile">
          <h3 class="anchor-mobile-title">夢想人物系列　影音故事</h3>
          <ul>
            <li v-for="item in profiles" :id="item.id" :key="item.id" @click.prevent="handle_scrollTo(item.title, item.idTo, item.isLock, item.id)" :class="{ shake: item.isLock }">
              <img :src="item.profile" alt="">
              <div class="describe">
                <p>{{ item.title }}</p>
                <p>{{ item.name }}</p>
              </div>
            </li>
          </ul>
        </div>
      
      <content-container>
      <br>
      <videoBox id="duncan" :videoInfo="videosInfo[0]"></videoBox>
      <br>
      <videoBox id="br" :videoInfo="videosInfo[1]"></videoBox>
      <br>
      </content-container>
      <content-container  style="background-image: linear-gradient(to bottom, #f2f2f2, rgba(255, 255, 255, 0));padding-top: 1px;">
      <div class="share-and-logo"> 
        <div class="share">
          <share href="https://udn.com/upf/ubrand/2019_data/DaretoDream/index.html"></share>
        </div>
        <div class="logo">
          <logo use-ubrand="yes" use-vision='no'>
            <div>
              <img :src="logoDown" alt="">
            </div>         
          </logo>
        </div>
      </div>
      <p><br></p>
      <editor>
        <div>製作人：盧巧梅</div>
        <div>文字採訪：盧巧梅、林筱穎</div>
        <div>影音製作：劉宜峰</div>
        <div>視覺設計：呂宗原</div>
        <div>網頁製作：胡凈悟</div>
        <div>議題行銷：張乃文、陳欣媛、王敏霏</div>
        <div>監製：潘如瑩、董谷音、蔡幸怡、陳曼薇</div>
        <div>2019.2.15</div>
      </editor>
      <p><br></p>
      <fb-comment href="https://udn.com/upf/ubrand/2019_data/DaretoDream/index.html"></fb-comment>
    </content-container>
    <back-top></back-top>
    <foot></foot>
  </div>
</template>

<script>
import Vue from 'vue'
import srcRWD from '@/mixin/srcRWD.js'
import globalComponents from '@/plugins/baseComponents.js'
import videoBox from '@/components/videoBox.vue'
import _throttle from 'lodash.throttle'

Vue.use(globalComponents)

export default {
  name: 'App',
  mixins: [srcRWD],
  data () {
    return {
      imgHeight: '100px',
      cover: require('@/../static/cover.png'),
      coverWeb: require('@/../static/cover_web.png'),
      coverTitle: require('@/../static/cover_title.svg'),
      logo: require('@/../static/logo_web.svg'),
      logoDown: require('@/../static/logo.png'),
      hotVideo: 'https://udn.com/upf/ubrand/2019_data/DaretoDream_Duncan/index.html',
      profiles: [
      {
        id: 'duncan_btn',
        idTo: 'duncan',
        title: '圖文創作者',
        name: 'Duncan',
        profile: require('@/../static/profiles/duncan.png'),
        profile_web: require('@/../static/profiles/duncan_web.png'),
        isLock: false
      },
      {
        id: 'br_btn',
        idTo: 'br',
        title: '饒舌歌手',
        name: 'BR',
        profile: require('@/../static/profiles/br.png'),
        profile_web: require('@/../static/profiles/br_web.png'),
        isLock: false
      },
      {
        id: 'anonymous1_btn',
        idTo: 'anonymous1',
        title: '3月',
        name: '即將推出',
        profile: require('@/../static/profiles/lock.png'),
        profile_web: require('@/../static/profiles/lock_web.png'),
        isLock: true
      },
      {
        id: 'anonymous2_btn',
        idTo: 'anonymous2',
        title: '4月',
        name: '即將推出',
        profile: require('@/../static/profiles/lock.png'),
        profile_web: require('@/../static/profiles/lock_web.png'),
        isLock: true
      },
      {
        id: 'anonymous3_btn',
        idTo: 'anonymous3',
        title: '5月',
        name: '即將推出',
        profile: require('@/../static/profiles/lock.png'),
        profile_web: require('@/../static/profiles/lock_web.png'),
        isLock: true
      },
      {
        id: 'anonymous4_btn',
        idTo: 'anonymous4',
        title: '6月',
        name: '即將推出',
        profile: require('@/../static/profiles/lock.png'),
        profile_web: require('@/../static/profiles/lock_web.png'),
        isLock: true
      }],
      videosInfo: [
        {
          id: 'duncan',
          name: '－Duncan－',
          number: '01',
          slogan: '有生之年，要畫出一幅<br>讓世界看見的作品',
          img: require('@/../static/flag1.png'),
          img_web: require('@/../static/flag1_web.png'),
          linkTo: 'https://udn.com/upf/ubrand/2019_data/DaretoDream_Duncan/index.html',
          video: 'https://www.youtube.com/embed/GwF4fFnxTkg'
        },
        {
          id: 'br',
          name: '－BR－',
          number: '02',
          slogan: '嘻哈是我畢生的事業<br>我要衝出台灣',
          img: require('@/../static/flag2.png'),
          img_web: require('@/../static/flag2_web.png'),
          linkTo: 'https://udn.com/upf/ubrand/2019_data/DaretoDream_BR/index.html',
          video: 'https://www.youtube.com/embed/p54sxKiKghM'
        }
      ]
    }
  },
  methods: {
    handle_scrollTo: _throttle(function (title, idTo, isLock, id_btn) {

      let label = "[DaretoDream][" + idTo + "][內滾到" + idTo + "]"

      if(isLock) {
        
        label = "[DaretoDream][" + idTo + "][目前無內滾]"

        window.ga("send", {
          "hitType": "event",
          "eventCategory": "OptionButton",
          "eventAction": "click",
          "eventLabel": label
        })

        console.log("It will sent:" + label)
        this.handle_shake(id_btn)
      } else {

        window.ga("send", {
          "hitType": "event",
          "eventCategory": "OptionButton",
          "eventAction": "click",
          "eventLabel": label
        })

        console.log("It will sent:" + label)
        $('html, body').animate({ scrollTop: $('#' + idTo).offset().top - 25 }, 1333)
      }

    }, 1000, {leading: true, trailing: false}),
    handle_shake (id_btn) {
      console.log("#" + id_btn)
      $("#" + id_btn).effect( "shake" );
    }
  },
  components: {
    videoBox
  },
  mounted () {}
}
</script>

<style  lang="scss">
@import './assets/CSS/theme.css';
@import './assets/CSS/UdnFontSize.css';

html, body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Microsoft JhengHei;
  font-weight: bold;
  p {
    margin: 0;
  }
    .cover {
      position: relative;
      background-repeat: no-repeat;
      background-size: cover;
      background-position: center;
      height: 100vh;
      .main-cover {
        width: 100%;
        @media screen and (min-width: 1440px) {
          display: none;
        }
      }
      .cover-title {
        position: absolute;
        left: 50%;
        top: 55%;
        transform: translate(-50%, -50%);
        width: 80%;
        @media screen and (min-width: 768px) and (max-width: 1023px) {
          width: 75%;
        }
        @media screen and (min-width: 1024px) {
          width: 40%;
        }
      }
      .logo {
        position: absolute;
        width: 80px;
        right: 15px;
        bottom: 35px;
        @media screen and (min-width: 768px) and (max-width: 1023px) {
          width: 130px;
          bottom: 50px;
        }
        @media screen and (min-width: 1024px) {
          width: 150px;
        }
      }
    }
    .title-track-same-month {
      .content {
          position: relative;
          margin: 0;
          @media screen and (min-width: 768px) and (max-width: 1023px) {
            text-align: center;
          }
          @media screen and (min-width: 1024px) {
            text-align: center;
          }
          
          .content-item {
            display: inline-block;
          }
          a {
            width: 100%;
            height: 100%;
            text-decoration: none;
            color: black;
            text-align: left;
            display: flex;
            .new {
            width: 17%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            background-color: #e60414;
            @media screen and (min-width: 768px) and (max-width: 1023px) {
              width: 25%;
              font-size: 40px;
            }
            @media screen and (min-width: 1024px) {
              width: 15%;
              font-size: 40px;
            }
          }
          .slogan {
            width: 85%;
            background-color: #f8f8f8;
            @media screen and (min-width: 768px) and (max-width: 1023px) {
              color: black;
            }
            @media screen and (min-width: 1024px) {
              color: black;
            }
            h3 {
                margin: 0;
                padding: 5px 10px 7px 11px;
                line-height: 1.25;
                font-family: 微軟正黑體;
                font-weight: bold;
                letter-spacing: -0.6px;
                text-align: left;
                font-size: 20px;
                @media screen and (min-width: 768px) and (max-width: 1023px) {
                  font-size: 30px;
                  line-height: 1.4;
                  margin: 15px 10px;
                  padding: 9px 0 12px 20px;
                }
                @media screen and (min-width: 1024px) {
                  font-size: 50px;
                  line-height: 1.4;
                  margin: 0 20px;
                  padding: 9px 0 12px 20px;
                }
            }
          }
        }
      }
    }
    .anchor-web {
      @media screen and (max-width: 768px) {
        display: none;
      }
      .anchor-web-title {
        padding: 55px 0;
        font-size: 37.9px;
        font-weight: bold;
        text-align: center;
        margin: 0;
      }
      ul {
        display: flex;
        justify-content: space-between;
        margin:0;
        padding: 0;
        text-indent: 0;
        list-style-type: 0;
        li {
          overflow: hidden;
          width: 110px;
          height: auto;
          display: flex;
          align-items: center;
          justify-content: center;
          flex-direction: column;
          position: relative;
          img {
            width: 100%;
            min-height: 110px;
            cursor: pointer;
            border-radius: 51%;
          }
          p {
            margin: 0;
            line-height: 1;
            text-align: center;
            font-size: 17px;
            line-height: 1.35;
            font-weight: bolder;
          }
          .locked {
            background-color: gray;
            width: 100%;
            height: 100%;
            position: absolute;
          }
        }
        .shake:hover, .shake:active {
            animation: shake 0.82s cubic-bezier(.36,.07,.19,.97) both;
            transform: translate(0, 0);
            // backface-visibility: hidden;
            perspective: 1000px;
          }
          @keyframes shake {
            10%, 90% {
              transform: translate(1px, 0);
            }
            
            20%, 80% {
              transform: translate(2px, 0);
            }

            30%, 50%, 70% {
              transform: translate(-4px, 0);
            }

            40%, 60% {
              transform: translate(4px, 0);
            }
          }
      }
    }
   .anchor-mobile {
     background-image: linear-gradient(to bottom, #f2f2f2, rgba(255, 255, 255, 0));
      @media screen and (min-width: 1024px) {
        display: none;
      }
      .anchor-mobile-title {
        padding: 27px 0;
        font-size: 25px;
        font-weight: 900;
        text-align: center;
        color: black;
        margin: 0;
      }
     ul {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        margin:0;
        padding: 0;
        text-indent: 0;
        list-style-type: 0;
        li {    
          overflow: hidden;
          width: 30%;
          display: flex;
          align-items: center;
          justify-content: center;
          position: relative;
          margin: 5px 0;
          flex-direction: column;
          @media screen and (min-width: 768px) and (max-width: 1023px) {
            width: 15%;
            height: auto;
          }
          img {
            width: 65%;
            cursor: pointer;
            border-radius: 51%;
            margin: 5px;
          }
          p {
            margin: 0;
            line-height: 1;
            text-align: center;
            font-size: 12px;
            line-height: 1.33;
            font-weight: bolder;
          }
          .locked {
            background-color: gray;
            width: 100%;
            height: 100%;
            position: absolute;
          }
        }
        .shake:hover, .shake:active {
            animation: shake 0.82s cubic-bezier(.36,.07,.19,.97) both;
            transform: translate3d(0, 0, 0);
            backface-visibility: hidden;
            perspective: 1000px;
          }
          @keyframes shake {
            10%, 90% {
              transform: translate3d(-1px, 0, 0);
            }
            
            20%, 80% {
              transform: translate3d(2px, 0, 0);
            }

            30%, 50%, 70% {
              transform: translate3d(-4px, 0, 0);
            }

            40%, 60% {
              transform: translate3d(4px, 0, 0);
            }
          }
      }
    }
  .share-and-logo {
      display: flex;
      justify-content: flex-start;
      flex-direction: column;
      margin-top: 15px;
      @media (min-width: 768px) and (max-width: 1024px){
        justify-content: space-between;
        flex-direction: row;
      }
      @media screen and (min-width: 1025px){
        justify-content: space-between;
        flex-direction: row;
      }
      .share {
            min-width: 35%;
      }
      .logo {
        @media (min-width: 768px) and (max-width: 1024px){
          margin-top: -5px;
        }
        @media screen and (min-width: 1025px){
          margin-top: -5px;
        }
      }
    }
}
</style>
