<template>
  <div>
    <Header></Header>
    <!-- slider -->
    <div class="flash">
      <div class="wrapper">
        <swiper :options="swiperOption" class="swiper-container">
          <!-- slides -->
          <swiper-slide class="swiper-item" v-for="item of swiperList" :key="item.id">
            <img class="swiper-img" :src="item.image" :alt="item.alt"/>
          </swiper-slide>
          <!-- Optional controls -->
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </div>
    </div>
    <!-- notice -->
    <div class="center_menu">
      <div class="container">
        <div class="row">
          <div class="col-xs-12 col-sm-12 col-md-12">
            <span class="center_name">新闻资讯</span>
            <div id="gd">
              <div id="gdli1">
                <ul id="gdli2">
                  <li v-for="item in noticeList">
                    <a :href="item.url" target="_self">{{item.title}}</a>
                  </li>
                </ul>
                <ul id="gdli3"></ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- product -->
    <div class="container">
      <div class="row">
        <div class="col-xs-12 col-sm-12 col-md-12">
          <div class="product_index">
            <div class="product_head" data-move-y="-40px">
              <h2>产品中心</h2>
              <p>PRODUCT DISPLAY</p>
            </div>
            <div class="product_list">
              <div class="col-sm-4 col-md-4 col-mm-6 product_img" v-for="item in productList">
                <a :href="item.url">
                  <img :src="item.image" class="img-thumbnail" :alt="item.title">
                </a>
                <p class="product_title">
                  <a :href="item.url" :title="item.title">{{item.title}}</a>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- link -->
    <Link></Link>
    <!-- footer -->
    <Footer></Footer>
  </div>
</template>

<script>
  import "swiper/css/swiper.css";
  import "bootstrap/dist/css/bootstrap.min.css";
  import "bootstrap/dist/js/bootstrap.min.js";
  import Header from "../../components/header";
  import Link from "../../components/link";
  import Footer from "../../components/footer";
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
            id: "10001",
            image: "/static/img/0ec56be68e7a842dad9deecf031fb5e2.jpg",
            alt: "解决方案"
          },
          {
            id: "10002",
            image: "/static/img/828e1f68597f57909393621a86888d0c.png",
            alt: "多年经验，专注软件技术开发"
          }
        ],
        // 公告
        noticeList: [{
          title: "诚信 -- 诚信是发展的基础，信守诚信企业的责任。",
          url: "#"
        }],
        // 产品列表
        productList: [{
          url: "#",
          image: "/static/img/6xh59ziv5dp66wvzacvrtxawmrce8dwy.png",
          title: "企业数据中台系统"
        }, {
          url: "#",
          image: "/static/img/7hl3bmsa871rldpnx5ewltyepxn0pqlr.png",
          title: "渠道营销管理系统"
        }, {
          url: "#",
          image: "/static/img/7gbquuosucpkhy2pq0ihbb5lm29smkmk.jpg",
          title: "企业网站设计"
        }]
      }
    },
    components: {
      Footer,
      Link,
      Header,
      swiper,
      swiperSlide
    },
    mounted() {
      this.trundle();
    },
    methods: {
      trundle() {
        let speed = 30;
        let tab = document.getElementById("gd");
        let tab1 = document.getElementById("gdli2");
        let tab2 = document.getElementById("gdli3");
        tab2.innerHTML = tab1.innerHTML;

        function Marquee() {
          if (tab2.offsetWidth - tab.scrollLeft <= 0)
            tab.scrollLeft -= tab1.offsetWidth
          else {
            tab.scrollLeft++;
          }
        }

        let MyMar = setInterval(Marquee, speed);
        tab.onmouseover = function () {
          clearInterval(MyMar)
        };
        tab.onmouseout = function () {
          MyMar = setInterval(Marquee, speed)
        };
      }
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

  /* 公告 */
  .center_menu {
    font-size: 14px;
    color: #7C98A2;
    width: 100%;
    height: 60px;
    line-height: 60px;
    border-bottom: 1px #ddd solid;
  }

  .center_name {
    display: inline-block;
    padding-left: 25px;
    background: url(../../assets/notice.png) left center no-repeat;
  }

  #gd {
    overflow: hidden;
    width: 92%;
    font-size: 12px;
    line-height: 60px;
    height: 60px;
    float: right;
  }

  #gd a {
    color: #333;
    margin-right: 10px;
    padding-left: 18px;
    background: url(../../assets/sign.png) left center no-repeat;
  }

  #gdli1 {
    float: left;
    height: 60px;
    width: 800%;
  }

  #gdli2, #gdli3, #gdli2 li, #gdli3 li {
    float: left;
  }

  /*首页产品*/
  .product_bg {
    padding-top: 30px;
    padding-bottom: 30px;
  }

  .product_head {
    display: block;
    background: url(../../assets/product-bg.png) no-repeat center center;
  }

  .product_head h2 {
    font-size: 32px;
    /*font-weight: bold;*/
    text-align: center;
    color: #38383A;
    margin: 0px;
  }

  .product_head p {
    font-family: 'Times New Roman';
    text-align: center;
    padding-top: 2px;
    font-size: 16px;
    color: #3B3C3E;
    margin-bottom: 5px;
  }

  .product_index {
    margin: 45px 0px 0px 0px;
  }

  .product_list {
    clear: both;
    padding: 30px 0px 0px 0px;
    margin-right: -15px;
    margin-left: -15px;
  }

  .product_list2 {
    padding-top: 30px;
  }

  .product_img {
    padding-left: 15px;
    padding-right: 15px;
    min-height: 200px;
  }

  .product_img img {
    margin-right: auto;
    margin-left: auto;
    display: block;
    max-width: 100%;
    height: auto;
    margin-bottom: 10px;
    max-height: 320px;
  }

  .product_list2 div.product_img {
    min-height: 220px;
  }

  .product_title {
    text-align: center;
    padding: 0px 15px 0px 0px;
    height: 40px;
  }

  .product_title a {
    color: #656464;
  }

  .product_title a:hover {
    text-decoration: none;
    color: #DA2625;
  }

  /*大屏幕*/
  @media screen and (min-width: 769px) {
    .flash {
      margin-top: 95px;
    }
  }
</style>
