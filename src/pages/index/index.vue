<template>
  <div class="page">

    <!-- Preloader -->
    <TheLoader v-if="isLoading"></TheLoader>
    <!-- /Preloader -->

    <div v-if="!isLoading" style="height: 100%;">
      <!-- Header and Navigation -->
      <TheHeader></TheHeader>
      <!-- /Header and Navigation -->

      <!-- Swiper -->
      <section class="slide-wrapper">
        <swiper class="slide" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
                :duration="duration"
                :circular="circular" @change="swiperChange" @animationfinish="animationfinish">
          <div v-for="item in imgUrls" :key="index">
            <swiper-item>
              <image :src="item" class="slide-image"/>
            </swiper-item>
          </div>
        </swiper>
        <div class="big-logo">
          <div>The</div>
          <h1>Wedding</h1>
          <h2>Inna &amp; Andre</h2>
        </div>
      </section>
      <!-- /Swiper -->

      <!-- Section - About -->
      <section class="about-us">
        <div class="container">
          <h2 class="text-center">新郎 &amp; 新娘</h2>
          <div class="devider">
            <img src="https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/devider.png" alt="devider">
          </div>
          <p class="about-info">
            Hello friends, we cant wait to celebrate our wedding in gods own country on 29 April 2013. We would love to
            have your gracious presence on this occassion. Please plan your travel and book tickets in advance and get
            ready for the party.
          </p>

          <img class="about-img" src="https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/about-us.png"
               alt="about-us">
        </div>
      </section>
      <!-- /Section - About -->

      <!-- Section - CountDown -->
      <section class="count-down">
        <div class="container">
          <h2 class="text-center">婚礼时间</h2>
          <div class="devider">
            <img src="https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/devider.png" alt="devider">
          </div>
          <p class="about-info" style="margin: 60rpx 0;">
            友情提示，请合理规划好您的行程 D:）
          </p>

          <div id="timer" class="text-center">
            <div class="timer-item">
              <span class="days digit"><span>-</span><span>2</span><span>2</span><span>7</span></span>
              <div class="smalltext">天</div>
            </div>
            <div class="timer-item">
              <span class="hours digit"><span>1</span><span>9</span></span>
              <div class="smalltext">时</div>
            </div>
            <div class="timer-item">
              <span class="minutes digit"><span>4</span><span>1</span></span>
              <div class="smalltext">分</div>
            </div>
            <div class="timer-item">
              <span class="seconds digit"><span>5</span><span>5</span></span>
              <div class="smalltext">秒</div>
            </div>
          </div>
        </div>
      </section>
      <!-- /Section - Location -->

      <!-- Section - CountDown -->
      <section class="location">
        <div class="container">
          <h2 class="text-center">婚礼地点</h2>
          <div class="devider">
            <img src="https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/devider.png" alt="devider">
          </div>
          <p class="about-info" style="margin: 60rpx 0;">
            友情提示，请合理规划好您的行程 D:）
          </p>

          <map id="map"
               :longitude="longitude"
               :latitude="latitude"
               scale="16"
               bindcontroltap="controltap"
               :markers="markers"
               bindmarkertap="markertap"
               show-location
               bindtap="click">
          </map>

        </div>
      </section>
      <!-- /Section - Location -->

      <!-- Footer -->
      <TheFooter></TheFooter>
      <!-- /Footer -->

    </div>

  </div>
</template>

<script>
  import TheLoader from '../../components/theLoader'
  import TheHeader from '../../components/theHeader'
  import TheFooter from '../../components/theFooter'
  import happyWeddingImg from '../../../static/images/happy-wedding.png'

  export default {
    // 组件名
    name: 'index',
    // 组件属性
    props: {},
    // 组件数据
    data () {
      return {
        isLoading: true,
        indicatorDots: true,
        autoplay: true,
        interval: 5000,
        duration: 900,
        circular: true,
        imgUrls: [
          'https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/slider1.png',
          'https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/slider2.png'
        ],
        longitude: 121.060429,
        latitude: 31.387403,
        markers: [
          {
            iconPath: happyWeddingImg,
            id: 0,
            latitude: 31.387403,
            longitude: 121.060429,
            width: 35,
            height: 45,
            callout: {
              display: 'ALWAYS',
              content: '婚礼地点',
              borderRadius: '5px',
              bgColor: '#e06175',
              color: '#fff',
              padding: 10
            }
          }]
      }
    },
    // 组件过滤器
    filters: {},
    // 组件计算属性
    computed: {
      isLoading: () => {
        return this.isLoading
      }
    },
    // 组件挂载
    components: {
      TheLoader,
      TheHeader,
      TheFooter
    },
    // 钩子函数
    beforeCreate () {
    },
    mounted () {
      setTimeout(() => {
        this.pageLoaded()
      }, 1000)
    },
    destroyed () {
    },
    watch: {},
    methods: {
      swiperChange (e) {
        console.log('第' + e.mp.detail.current + '张轮播图发生了滑动')
      },
      animationfinish (e) {
        console.log('第' + e.mp.detail.current + '张轮播图滑动结束')
      },
      pageLoaded () {
        this.isLoading = false
      },
      click () {
        console.log(1)
      }
    }
  }
</script>

<style scoped>
  .slide-wrapper {
    position: relative;
    width: 100%;
    height: calc(100% - 140rpx);
  }

  .slide {
    width: 100%;
    height: 100%;
  }

  .slide-image {
    width: 100%;
    height: 100%;
  }

  .big-logo {
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translate(-50%);
    color: #fff;
  }

  .devider > img {
    display: block;
    margin: 0 auto;
    width: 220rpx;
    height: 36rpx;
  }

  .about-info {
    text-indent: 2em;
    margin: 18rpx 0;
  }

  .about-img {
    display: block;
    margin: 0 auto;
    width: 400rpx;
    height: 400rpx;
  }

  /* -3.4. Countdown
-------------------------------------------------------------- */

  #timer {
    position: relative;
  }

  #timer > div.timer-item {
    display: inline-block;
    position: relative;
    margin: 0 14rpx;
    text-align: center;
  }

  @media screen and (max-width: 640px) {
    #timer > div.timer-item {
      display: block;
      margin-bottom: 20px;
    }
  }

  #timer > div.timer-item:first-child:after {
    content: "";
    background: url(https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/dots.png) no-repeat;
    display: block;
    width: 100rpx;
    height: 5px;
    position: absolute;
    top: 23px;
    left: -55px;
  }

  @media screen and (max-width: 640px) {
    #timer > div.timer-item:first-child:after {
      display: none;
    }
  }

  #timer > div.timer-item:last-child:after {
    content: "";
    background: url(https://lg-hko9gpjg-1253449358.cos.ap-shanghai.myqcloud.com/dots.png) no-repeat;
    display: block;
    width: 100rpx;
    height: 5px;
    position: absolute;
    top: 23px;
    right: -55px;
  }

  @media screen and (max-width: 640px) {
    #timer > div.timer-item:last-child:after {
      display: none;
    }
  }

  #timer .smalltext {
    color: #646465;
    font-size: 1em;
    line-height: 1.25em;
    padding-top: 10px;
  }

  .digit span {
    border-width: 1.49px;
    border-style: solid;
    border-color: #2d2d31;
    color: #484846;
    width: 52px;
    height: 52px;
    display: inline-block;
    border-radius: 52px;
    margin: 0 3px;
    font-size: 2.125em;
    line-height: 1.5em;
    text-align: center;
  }

  #map {
    position: relative;
    width: 100%;
    height: 600rpx;
  }

</style>
