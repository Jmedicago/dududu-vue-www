<template>
  <div>
    <Header></Header>
    <!-- slider -->
    <div class="flash">
      <div class="wrapper">
        <swiper :options="swiperOption" class="swiper-container">
          <!-- slides -->
          <swiper-slide class="swiper-item" v-for="item of swiperList" :key="item.id">
            <img class="swiper-img" :src="item.imgUrl" alt="去哪儿门票"/>
          </swiper-slide>
          <!-- Optional controls ,显示小点-->
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </div>
    </div>
  </div>
</template>

<script>
  import "swiper/css/swiper.css";
  import "bootstrap/dist/css/bootstrap.min.css";
  import "bootstrap/dist/js/bootstrap.min.js";
  import Header from "../../components/header";
  import {swiper, swiperSlide} from "vue-awesome-swiper";

  export default {
    data() {
      return {
        swiperOption: {
          // 参数选项,显示小点
          pagination: ".swiper-pagination",
          //循环
          loop: true,
          //每张播放时长3秒，自动播放
          autoplay: 2000,
          //滑动速度
          speed: 1000,
          // delay:1000
        },
        //三张轮播，使用变量循环
        swiperList: [
          {
            id: "001",
            imgUrl: "http://localhost:63342/h136/advs/pics/20190428/1556441135.jpg"
          },
          {
            id: "002",
            imgUrl: "http://localhost:63342/h136/advs/pics/20190428/1556441226.jpg"
          }
        ]
      }
    },
    components: {
      Header,
      swiper,
      swiperSlide
    }
  }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet
    width: 12px;
    height: 12px;
    border: 1px solid #fff;
    opacity: unset;
    background: unset;

  .wrapper >>> .swiper-pagination-bullet-active
    background: #fff

  .flash img {
    width: 100%
  }

  .flash ul.bxslider {
    list-style: none;
  }

  .flash div.bx-pager {
    bottom: 4%;
  }

  .flash div.bx-controls-direction {
    display: none;
  }

  .img-thumbnail {
    border: none;
  }

  .img-thumbnail:hover, .opacity_img:hover {
    opacity: 0.8;
  }

  /*大屏幕*/
  @media screen and (min-width: 769px) {
    .flash {
      margin-top: 95px;
    }
  }
</style>
