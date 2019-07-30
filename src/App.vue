<template>
  <div id="app">
    <v-header :seller='seller'></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <!-- router-link 相当于a标签， to="/goods"跳去goods路由-->
        <router-link to="/goods">商品</router-link> 
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link> 
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link> 
      </div>
    </div>
    <!-- 路由入口传的数据。通过这个路由跑的页面都能传得到数据 -->
    <router-view :seller="seller"></router-view>
  </div>
</template>

<script>
import header from '@/components/header/header.vue'
export default {
  name: 'App',
  
  data () {
    return {
      seller: {
        // 从api获取
      }
    }
  },
  components: {
    'v-header': header
  },
  created () {
    this.$http.get('https://www.easy-mock.com/mock/5d01b444d75bbf0fd8c88d19/vue-eleme/vue-eleme')
      .then(res => {
        console.log(res)
        if (res.data.errno === 0) {
          this.seller = Object.assign({}, this.seller, res.data.data)
        }
      })
  }
}
</script>

<style lang="stylus">
@import './common/stylus/mixin.styl'
.tab
  display flex
  width 100%
  height 40px
  line-height 40px
  border-bottom 1px solid rgba(7, 17, 27, 0.1)
  border-1px(rgba(7, 17, 27, 0.1))
  .tab-item
    flex 1
    text-align center

    & > a
      display block
      font-size 14px
      color rgb(77, 85, 93)
      text-decoration none

      &.router-link-active
        color rgb(240, 20, 20) //点哪个tabbar哪个就会标红
</style>
