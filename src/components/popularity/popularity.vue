<template lang="html">
<div class="popularity">
  <div class="popularity-header">
    <strong>
      <span class="">o</span>
      <div class="menu-item" :class="{'current':selected === index}" v-for="(item,index) in menuList" @click="select(index)" :key="index">
        {{item}}
      </div>
    </strong>
    <div v-for="(movie,index) in movies" :key="index">
      {{movie.title}}
    </div>
  </div>
</div>
</template>

<script type="text/ecmascript-6">
export default {
  data() {
    return {
      selected: 0,
    };
  },
  props: {
    menuList: {
      type: Array,
      default() {
        return ['最新收录', '热门电影', '热门电视'];
      },
    },
    movies: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    select(i) {
      this.selected = i;
    },
  },
};
</script>

<style lang="stylus" ref="stylesheet/stylus">
.popularity
  .popularity-header
    font-size 14px
    line-height 20px
    color rgba(7,17,27,0.5)
    border-bottom .5px solid rgb(0,0,0)
    .menu-item
      display inline-block
      margin-bottom -1px
      padding 3px 6px
      cursor: default
      &.current
        background #fff
        border 1px solid rgb(0,0,0)
        border-bottom 0px
        
</style>
