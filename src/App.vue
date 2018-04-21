<template>
  <div id="app">
    <transition name="header-fade">
    <header v-show="showheader" class="header">
      <div class="hearer-item"
      v-for="(item,index) in menulist" :key="index"
      :class="{'current':index === active}"
      @click="selectMenu(index)">
        <router-link class="test" to="/home">{{item}}</router-link>
      </div>
    </header>
    </transition>
    <div class="app-content">
      <router-view/>
    </div>
    <footer class="footer">
      iam footer
    </footer>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'App',
  data() {
    return {
      showheader: true,
      currentScrollY: 0,
      active: 0,
    };
  },
  created() {
    this.menulist = ['首页', '2', '3', '4'];
    window.addEventListener('scroll', () => {
      if (window.scrollY > this.currentScrollY) {
        this.showheader = false;
      } else {
        this.showheader = true;
      }
      this.currentScrollY = window.scrollY;
    });
  },
  methods: {
    selectMenu(i) {
      this.active = i;
    },
  },
};
</script>

<style lang="stylus" ref="stylesheet/stylus">
@import './common/stylus/base';
.banner
  position: fixed
.header
  position: fixed
  padding 0 10px
  width: 100%
  height 35px
  z-index: 1000
  top: 0
  left: 0
  background rgb(52, 99, 135)
  .hearer-item
    display inline-block
    text-align center
    width 60px
    font-size 14px
    line-height 14px
    color #fff
    padding 10px
    >a
      color #fff
      text-decoration none
    &:hover
      color rgb(52, 99, 135)
      background #fff
      >a
        color rgb(52, 99, 135)
    &.current
      color rgb(52, 99, 135)
      background #fff
      border-bottom 1px solid rgba(0,160,220,0.4)
      >a
        color rgb(52, 99, 135)
.app-content
   margin-top 35px
   padding 4px
   min-height 1000px
   background rgba(0,0,0,0.1)
.footer
  flex-shrink 0
  padding 6px
  height 80px
  background rgb(52, 99, 135)
@media (max-width: 700px)
  .app-content
    background #fff
</style>
