<template>
<div class="ratings" ref="ratings">
  <div class="header">
    <div class="header-left">
      <h1 class="score">{{seller.score}}</h1>
      <div class="title">综合评分</div>
      <div class="high">高于周边商家{{seller.rankRate}}%</div>
    </div>
    <div class="header-right">
      <div class="score-wrapper">
        <span class="title">服务态度</span>
        <star :score="seller.serviceScore" size="36"></star>
        <span class="score">{{seller.serviceScore}}</span>
      </div>
      <div class="score-wrapper">
        <span class="title">商品评分</span>
        <star :score="seller.foodScore" size="36"></star>
        <span class="score">{{seller.foodScore}}</span>
      </div>
      <div class="score-wrapper">
        <span class="title">送达时间</span>
        <span class="deliveryTime">{{seller.deliveryTime}}分钟</span>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import star from '@/components/star/star'
export default {
  name:'index',
  props: {
    seller: {
      type: Object
    }
  },
  data() {
    return {
      ratings: []
    }
  },
  components: {
    star
  },
}
</script>

<style lang="stylus" scoped>
 @import "../../common/stylus/mixin.styl"
  .ratings
    position absolute
    overflow hidden
    top 174rpx
    left 0
    width 100%
    .header
      display flex
      padding 18px 0
      .header-left
        flex 0 0 137px
        padding 6px 0
        width 137px
        border-right 1px solid rgba(7, 17, 27, 0.1)
        text-align center
        .score
          font-size 24px
          line-height 29px
          margin-bottom 6px
          color rgb(255, 153, 0)
        .title
          font-size 12px
          line-height 18px
          vertical-align top
          color: rgb(7, 17, 27)
          font-weight 700
        .high
          font-size 12px
          line-height 12px
          color rgb(147, 153, 159)
      .header-right
        flex 1
        padding 6px 20px
        .score-wrapper
          margin-bottom 8px
          .title
            display inline-block
            vertical-align top
            line-height 18px
            font-size 12px
            color rgb(7, 17, 27)
          .star
            // display inline-block
            vertical-align top
            margin 0 6px
          .score
            display inline-block
            right 10px
            vertical-align top
            font-size 12px
            line-height 18px
            color rgb(255, 153, 0)
          .deliveryTime
            display inline-block
            margin-left 12px
            font-size 12px
            color rgb(147, 153, 159)
</style>
