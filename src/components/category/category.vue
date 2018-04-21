<template lang="html">
<div class="category">
  <div class="category-header">
    <h1 class="title">
      <strong>
        <span class="icon">
          123123
        </span>
        <a class="text">
          {{title}}
        </a>
      </strong>
    </h1>
    <div class="more">
      <a href="" title="">更多>></a>
    </div>
  </div>
  <div class="category-movies-cotent">
    <thumbnail v-for="(movie,index) in movies"
    :key="index" :movie="movie">
    </thumbnail>
  </div>
</div>
</template>

<script type="text/ecmascript-6">
import thumbnail from '../thumbnail/thumbnail';

export default {
  props: {
    movies: {
      type: Array,
      default() {
        return [];
      },
    },
    title: {
      type: String,
      default() {
        return '';
      },
    },
  },
  components: {
    thumbnail,
  },
};
</script>

<style lang="stylus" ref="stylesheet/stylus">
.category
  margin: 5px 0;
  background-color: #fff;
  padding: 0px 10px;
  .category-header
    position relative
    margin: 0;
    line-height: 32px;
    font-size: 20px;
    border-bottom: 2px solid #eee;
    .title
      margin-left 1px
      box-sizing border-box
      >strong
        position relative
        padding-top 1px
        border-bottom: 2px solid #FF5E52;
        display: inline-block;
        bottom: -2px;
        font-weight: normal;
        .icon,.text
          display inline-block
          line-height: 32px;
          font-size: 20px;
    @media (max-width: 700px)
      .title
        line-height 13px
        >strong
          line-height 13px
          .icon,.text
            font-size: 15px;
            line-height 13px
            padding-bottom 5px
    .more
      position absolute
      right 0
      top 0
      margin-right: 10px;
      font-size: 13px;
      text-align: center;
      >a
        text-decoration none
    @media (max-width: 700px)
      .more
        line-height 22px
</style>
