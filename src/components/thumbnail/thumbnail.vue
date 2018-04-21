<template lang="html">
<div class="movie-item">
  <div class="movie-img">
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
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    movie: {
      type: Object,
    },
  },
};
</script>

<style lang="stylus" ref="stylesheet/stylus">
.movie-item
  display inline-block
  position relative
  padding-bottom 3px
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
</style>
