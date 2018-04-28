<template>
  <div class="tab">
    <router-link v-for="(item, index) in listTab" :key="index" tag="div" class="tab-item" :to="item.tolink">
      <span class="tab-link">{{item.title}}</span>
    </router-link>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  data () {
    return {
      listTab: [
        {title: '推荐', tolink: '/recommend'},
        {title: '歌手', tolink: '/singer'},
        {title: '排行', tolink: '/rank'},
        {title: '搜索', tolink: '/search'}
      ]
    }
  }
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"
  .tab
    display: flex
    height: 44px
    line-height: 44px
    font-size: $font-size-medium
    .tab-item
      flex: 1
      text-align: center
      .tab-link
        padding-bottom: 5px
        color: $color-text-l
      &.router-link-active
        .tab-link
          color: $color-theme
          border-bottom: 2px solid $color-theme
</style>
