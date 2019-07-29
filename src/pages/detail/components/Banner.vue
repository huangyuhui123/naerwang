<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img :src="bannerImg" alt="" class="banner-img">
            <div class="banner-info">
                <div class="banner-title">{{this.sightName}}</div>
                <div class="banner-number">
                    <span class="iconfont banner-icon">&#xe634;</span>
                    {{this.bannerImg.length}}
                </div>
            </div>
        </div>
        <common-gallary :imgs="gallaryImgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
    </div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallary: false,
      imgs: [
        'https://img1.qunarzz.com/vs_ceph_vs_tts/2832024d-dfe1-4999-b426-497ef7971e3d.jpg_r_640x420x90_56057c8e.jpg',
        'https://img1.qunarzz.com/vs_ceph_vs_tts/2832024d-dfe1-4999-b426-497ef7971e3d.jpg_r_640x420x90_56057c8e.jpg'
      ]
    }
  },
  components: {
    CommonGallary
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
  }
}
</script>
<style lang="stylus" scoped>
.banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
        width: 100%
    .banner-info
        display: flex
        position: absolute
        left: 0
        right: 0
        bottom: 0
        line-height: .6rem
        color: #fff
        background-image: linear-gradient(top, rgba(0,0,0,0),rgba(0,0,0,.8))
        .banner-title
            flex: 1
        .banner-number
            padding: 0 .4rem
            height: .32rem
            line-height: .32rem
            border-radius: .2rem
            background: rgba(0,0,0, .8)
            font-size: .24rem
            margin-top: .14rem
            .banner-icon
                font-size: .24rem
</style>
