<template>
    <div class="icons">
        <div class="icon">
            <img src="http://s.qunarzz.com/touch_home/images/entrances.png" alt="">
            <p>热门推荐</p>
        </div>
    </div>
</template>
<script>
export default {
    name: 'HomeIcons'
}
</script>
<style lang="stylus" scoped>
    .icons
        overflow: hidden
        height: 0
        padding-bottom: 50%
        background: #fff
        .icon
            float: left
            width: 25%
            padding-bottom: 25%
            background: red
</style>
