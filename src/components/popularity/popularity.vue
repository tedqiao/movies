<template lang="html">
<div class="popularity">
  <div class="popularity-header">
    <strong>
      <span class="">o</span>
    </strong>
    <div class="menu-item"
    :class="{'current':selected === index}"
    v-for="(item,index) in menuList"
    @click="select(index)" :key="index">
      {{item}}
    </div>
  </div>
  <div class="popularity-body">
    <div class="movie-item" v-for="(movie,index) in movies" :key="index">
      <div  class="movie-img">
        <img :src="movie.images.small" alt=""/>
      </div>
      <h2 class="movie-title">
        {{movie.title}}
      </h2>
      <div class="release-year">
        <span>首映时间 {{movie.year}}</span>
      </div>
      <div v-show="movie.rating.average" class="rating">
        <span class="number">{{movie.rating.average}}分</span>
      </div>
    </div>
  </div>
  <div v-show="btn" class="show-more">
    <a class="show-more-btn" href="">查看今天更新内容</a>
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
    btn: {
      type: Boolean,
      default: false,
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
  background #fff
  margin-top 20px
  padding 0 10px
  .popularity-header
    position relative
    padding 15px 5px 0px 5px
    font-size 14px
    line-height 20px
    color rgba(7,17,27,0.5)
    border-bottom 1px solid rgb(0,0,0)
    .menu-item
      display inline-block
      padding 3px 15px
      cursor: default
      &.current
        position relative
        background #fff
        bottom -1px
        border 1px solid rgb(0,0,0)
        border-bottom 1px solid rgb(255,255,255)
    .line
      position absolute
      width 100%
      border-bottom 1px solid rgb(0,0,0)
      bottom 0px
    @media (max-width: 400px)
      .menu-item
        padding 3px 3px
  .popularity-body
    padding 10px 0
    font-size 0px
    width 100%
    .movie-item
      display inline-block
      position relative
      margin-top 5px
      width calc(100%  /6)
      &:hover
        box-shadow: 0px 2px 2px #CCC;
        outline: 1px solid #DDD;
      .movie-img
        padding 5px
        >img
         width:100%
         height 100%
      .movie-title
        margin 5px 0
        font-size 14px
        text-align center
        font-weight bolder
      .release-year
        text-align center
        font-size 12px
        color #666666
      .rating
        position absolute
        top 5px
        right 5px
        .number
          display: inline-block;
          background-color: #bb9b6a;
          border-bottom-left-radius: 5px;
          border-bottom-right-radius: 5px;
          padding: 0 5px;
          opacity: .95;
          margin-right: 5px;
          font-size: 12px;
          text-align: center;
          color: #fff;
          line-height: 23px;
    @media (max-width: 700px)
      .movie-item
        width calc(100%  /3)
  .show-more
    .show-more-btn
      text-decoration none
      width: 100%;
      color: #fff;
      background-color: #346387;
      display: inline-block;
      padding: 5px 0;
      font-size: 14px;
      font-weight: 400;
      line-height: 1.42857143;
      text-align: center;
      border: 1px solid transparent;
      border-radius: 4px;
      margin-top: 5px;
@media (max-width: 700px)
  .popularity
    background #fff
    margin-top 10px
    padding 0 10px
    .popularity-header
      padding 5px 5px 0px 5px
</style>
