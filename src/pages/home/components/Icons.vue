<template>
  <div class="icons">
    <swiper>
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
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      iconList: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
        desc: '景点门票'
      },
      {
        id: '0002',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
        desc: '动植物园'
      },
      {
        id: '0003',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/87/20656da0ac042002.png',
        desc: '玻璃栈道'
      },
      {
        id: '0004',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/338c5b924c5809e8c7b14f60a953c3e2.png',
        desc: '深圳欢乐谷'
      },
      {
        id: '0005',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/184e261814a5d07a5d3d08cd29cf590d.png',
        desc: '长隆度假区'
      },
      {
        id: '0006',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/4573132ba33603c8c3dbacc4d46a1ac6.png',
        desc: '罗浮山'
      },
      {
        id: '0007',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/cba147cf6cfcea7109d0bff6aac6f626.png',
        desc: '香市动物园'
      },
      {
        id: '0008',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/90/59a2f523ee2f9202.png',
        desc: '隐贤山庄'
      },
      {
        id: '0009',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/a6/6d97515091789602.png',
        desc: '世界之窗'
      },
      {
        id: '0010',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
        desc: '东莞必游'
      }]
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
  @import '~styles/varibles.styl';
  @import '~styles/mixins.styl';
  .icons >>> .swiper-container
    height 0
    padding-bottom 50%
  .icons
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
