<template>
    <div class="icons">
        <swiper  >
            <swiper-slide v-for="(page, index) of pages" :key="index">
                <div class="icon"
                    v-for="item of page"
                    :key = "item.id"
                >
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" alt="" />
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>
<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      iconList: [
        {
          id: '0001',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_2.jpg',
          desc: '景点门票'
        },
        {
          id: '0002',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_3.jpg',
          desc: '滑雪季'
        },
        {
          id: '0003',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_4.jpg',
          desc: '泡温泉'
        },
        {
          id: '0004',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_5.jpg',
          desc: '动物园'
        }, {
          id: '0005',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_6.jpg',
          desc: '植物园'
        }, {
          id: '0006',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_7.jpg',
          desc: '景点门票'
        }, {
          id: '0007',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_8.jpg',
          desc: '景点门票'
        }, {
          id: '0008',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_9.jpg',
          desc: '景点门票'
        }, {
          id: '0009',
          imgUrl: 'http://pic46.nipic.com/20140815/2531170_172548240000_1.jpg',
          desc: '一日游'
        }
      ]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
    .icons >>> .swiper-container
        height: 0
        padding-bottom: 50%
    .icon
        position: relative
        overflow hidden
        float: left
        width: 25%
        height: 0
        padding-bottom: 25%
        .icon-img
            position: absolute
            top: 0
            left: 0
            right: 0
            bottom: .44rem
            box-sizing: border-box
            padding: .1rem
            .icon-img-content
                height: 100%
                display block
                border-radius: 50%
                margin: 0 auto
        .icon-desc
            position: absolute
            left: 0
            right: 0
            bottom: 0
            height: .44rem
            line-height: .44rem
            text-align: center
            color: $darkTextColor
            ellipsis()
</style>
