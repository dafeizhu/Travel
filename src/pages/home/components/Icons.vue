<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide
      v-for="(page, index) of pages"
      :key="index"
      >
        <div class="icon"
        v-for="item of page"
        :key="item.id"
        >
          <div class="icon-img">
            <img class="icon-img-content" :src='item.imgUrl' />
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  props: {
    list: Array
  },
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
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
  @import '~styles/varibles.styl';
  @import '~styles/mixins.styl';
  .icons >>> .swiper-pagination-bullets
    width 100%
    position absolute
    bottom 0
  .icons >>> .swiper-pagination-bullet
    width .12rem
    height .12rem
  .icons >>> .swiper-container
    height 0
    padding-bottom 53%
  .icons
    position relative
    margin-top .1rem
    .icon
      position relative
      overflow hidden
      float left
      width 25%
      height 0
      padding-bottom 25%
      .icon-img
        position absolute
        top 0
        left 0
        right 0
        bottom .44rem
        box-sizing border-box
        padding .1rem
        .icon-img-content
          display block
          margin 0 auto
          height 100%
      .icon-desc
        position absolute
        bottom 0
        left 0
        right 0
        height .44rem
        line-height .44rem
        text-align center
        color $darkTextColor
        ellipsis()
</style>
