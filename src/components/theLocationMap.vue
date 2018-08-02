<template>
  <map id="map"
       :longitude="longitude"
       :latitude="latitude"
       scale="14"
       bindcontroltap="controltap"
       :markers="markers"
       bindmarkertap="markertap"
       bindregionchange="regionchange"
       show-location
       style="width: 750rpx; height: 350px;">
  </map>
</template>

<script>
  export default {
    // 组件名
    name: 'theLocationMap',
    // 组件构造
    mixins: [],
    // 组件扩展
    extends: {},
    // 组件属性
    props: {},
    // 组件数据
    data () {
      return {
        longitude: 116.487847,
        latitude: 40.002607,
        markers: [
          {
            id: 0,
            latitude: 40.002607,
            longitude: 116.487847,
            width: 35,
            height: 45
          }]
      }
    },
    // 组件过滤器
    filters: {},
    // 组件计算属性
    computed: {},
    // 组件挂载
    components: {},
    // 钩子函数
    beforeCreate () {
    },
    mounted () {
    },
    destroyed () {
    },
    watch: {},
    methods: {}
  }
</script>
<style scoped>

</style>