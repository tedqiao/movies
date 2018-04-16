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
 </div>
</div>
</template>

<script type="text/ecmascript-6">
import slider from 'vue-concise-slider';
import popularity from '../popularity/popularity';

export default {
  data() {
    return {
      pages: [
        {
          html: '<div class="slider-item">slider1</div>',
          style: {
            background: '#1bbc9b',
          },
        },
        {
          html: '<div class="slider-item">slider2</div>',
          style: {
            background: '#4bbfc3',
          },
        },
        {
          html: '<div class="slider-item">slider3</div>',
          style: {
            background: 'url(http://via.placeholder.com/350x150)',
          },
        },
      ],
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
    };
  },
  components: {
    slider,
    popularity,
  },
  methods: {
    slide(data) {
      console.log(data);
    },
    onTap(data) {
      console.log(data);
    },
    onInit(data) {
      console.log(data);
    },
  },
  created() {
    this.$http.get('http://localhost:3000/movies').then((res) => {
      const response = res.body;

      if (response.errno !== 0) {
        return;
      }

      this.movies = response.data;
      console.log(this.movies);
    });
  },
};
</script>

<style lang="stylus" ref="stylesheet/stylus">
.home-page
  .slider
    max-width 100%
    .slider-item
      padding-top 35%
  .content
    margin-top 40px
</style>
