<template lang="html">
<div class="home-page">
  <div class="slider">
      <slider ref="slider" :pages="pages" :sliderinit="sliderinit"
      @slide='slide' @tap='onTap' @init='onInit'>
          <div slot="loading">loading...</div>
      </slider>
 </div>
 <div class="content">
   <popularity :movies="movies.subjects"></popularity>
   <popularity :movies="movies.subjects" :menuList="newMenuList" :btn="true"></popularity>
 </div>
</div>
</template>

<script type="text/ecmascript-6">
import slider from 'vue-concise-slider';
import popularity from '../popularity/popularity';

export default {
  data() {
    return {
      pages: [],
      // Sliding configuration [obj]
      sliderinit: {
        currentPage: 0,
        thresholdDistance: 500,
        thresholdTime: 100,
        autoplay: 3000,
        loop: true,
        infinite: 1,
        slidesToScroll: 1,
        timingFunction: 'ease',
        duration: 300,
      },
      movies: [],
      newMenuList: [],
    };
  },
  components: {
    slider,
    popularity,
  },
  methods: {
    // slide(data) {
    //   console.log(data);
    // },
    // onTap(data) {
    //   console.log(data);
    // },
    // onInit(data) {
    //   console.log(data);
    // },
  },
  created() {
    this.$http.get('http://localhost:3000/movies').then((res) => {
      const response = res.body;

      if (response.errno !== 0) {
        return;
      }
      this.movies = response.data;
    });
    this.pages = [{
      html: '<div class="slider-item">slider1</div>',
      style: {
        background: 'url(http://ww4.sinaimg.cn/large0060lm7Tly1fm61fx42gvj30nw0a0tfe.jpg)',
      },
    },
    {
      html: '<div class="slider-item">slider2</div>',
      style: {
        background: 'url(http://ww3.sinaimg.cn/large/0060lm7Tly1fntrgop7ywj30nw0a0dn9.jpg)',
      },
    },
    {
      html: '<div class="slider-item">slider3</div>',
      style: {
        background: 'url(http://ww4.sinaimg.cn/large/0060lm7Tly1fm61fx42gvj30nw0a0tfe.jpg)',
      },
    }];

    this.newMenuList = ['今日更新', '电影', '电视剧', '综艺', '动漫'];
  },
};
</script>

<style lang="stylus" ref="stylesheet/stylus">
.home-page
  .slider
    max-width 100%
    .slider-item
      display block
      height 30px
      padding-top 35%
      background rgba(0,0,0,0.5)
  .content
    margin-top 40px
</style>
