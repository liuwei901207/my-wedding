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

      <div class="slide-wrapper">
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
      </div>
      <!-- /Swiper -->

    </div>

  </div>
</template>

<script>
  import TheLoader from '../../components/theLoader'
  import TheHeader from '../../components/theHeader'
  import TheFooter from '../../components/theFooter'

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
        ]
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
      }
    }
  }
</script>

<style scoped>
  .slide-wrapper {
    position: relative;
    padding-top: 73px;
    width: 100%;
    height: calc(100% - 73px);
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
</style>
