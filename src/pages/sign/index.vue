<template>
  <div class="page">
    SIGN
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
            height: 45
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
    width: 100%;
    height: 600rpx;
  }

</style>
