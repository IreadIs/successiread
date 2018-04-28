<template>
  <div id="app">
    <m-header></m-header>
    <tab></tab>
    <keep-alive>
      <transition :name="transitionName">
        <router-view></router-view>
      </transition>
    </keep-alive>
    <player></player>
  </div>
</template>

<script>
import Player from 'components/player/player'
import router from './router'
import MHeader from 'components/m-header/m-header'
import Tab from 'components/tab/tab'
export default {
  name: 'App',
  components: {
    MHeader,
    Tab,
    Player
  },
  data () {
    return {
      transitionName: 'slide-right'
    }
  },
  watch: {
    $route (to, from) {
      if (to.meta.index > from.meta.index) {
        this.transitionName = 'slide-right'
      } else {
        this.transitionName = 'slide-left'
      }
    },
    router
  }
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
@import "~common/stylus/variable"
.slide-right-enter-active,
.slide-right-leave-active,
.slide-left-enter-active,
.slide-left-leave-active {
  will-change: transform;
  transition: all 500ms;
  position: absolute;
}
.slide-right-enter {
  opacity: 0;
  transform: translate3d(-100%, 0, 0);
}
.slide-right-leave-active {
  opacity: 0;
  transform: translate3d(100%, 0, 0);
}
.slide-left-enter {
  opacity: 0;
  transform: translate3d(100%, 0, 0);
}
.slide-left-leave-active {
  opacity: 0;
  transform: translate3d(-100%, 0, 0);
}
</style>
