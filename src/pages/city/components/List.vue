<template>
    <div class="list" ref="wrapper">
        <div >
            <div class="area">
                <div class="title border-bottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{this.currentCity}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-bottom">热门城市</div>
                <div class="button-list">
                <div class="button-wrapper"
                 v-for="item of hot"
                 :key="item.id"
                 @click="handleCityClick(item.name)"
                 >
                    <div class="button">{{item.name}}</div>
                </div>
                </div>
            </div>
            <div class="area"
                v-for="(item,key) of cities"
                :key="key"
                :ref="key"
                >
                <div class="title border-bottom">{{key}}</div>
                <div class="item-list"
                 v-for="innerItem of item"
                  :key="innerItem.id"
                   @click="handleCityClick(innerItem.name)"
                  >
                    <div class="item border-bottom">{{innerItem.name}}</div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Bscroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    hot: Array,
    letter: String
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      console.log(this.letter)
      const element = this.$refs[this.letter][0]
      this.scroll.scrollToElement(element)
    }
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.border-bottom
    &:before
        border-color: #cccccc
    &:after
        border-color: #cccccc
.list
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    .title
        line-height: .54rem
        background: #eeeeee
        padding-left: .2rem
        color: #666
        font-size: .26rem
    .button-list
        overflow: hidden
        padding: .1rem .6rem .1rem .1rem
        .button-wrapper
            width: 33.33%
            float: left
            .button
                margin: .1rem
                padding: .1rem 0
                text-align: center
                border: .02rem solid #ccc
                border-radius: .06rem
    .item-list
        .item
            line-height: .76rem
            color: #666666
            padding-left: .2rem
</style>
