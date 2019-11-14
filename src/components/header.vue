<template>
  <header>
    <!-- fixed navbar -->
    <nav class="navbar navbar-default navbar-fixed-top">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar"
                  aria-expanded="false" aria-controls="navbar">
            <span class="sr-only"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a href="#">
            <img src="../assets/logo.png" class="logo" alt="黄冈市嘟嘟嘟网络科技有限公司"/>
          </a>
        </div>
        <div id="navbar" class="navbar-collapse collapse">
          <ul class="nav navbar-nav navbar-nav-c">
            <li :class="{dropdown : nav.child != null}" v-for="nav in navList">
              <a :href="nav.url">{{nav.name}}</a>
              <a :href="nav.url" v-if="nav.child != null" id="app_menudown" class="dropdown-toggle"
                 data-toggle="dropdown" role="button" aria-expanded="false">
                <span class="glyphicon glyphicon-menu-down btn-xs"></span>
              </a>
              <ul v-if="nav.child != null" class="dropdown-menu nav_small" role="menu">
                <li v-for="item in nav.child">
                  <a :href="item.url">{{item.name}}</a>
                </li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
  import "bootstrap/dist/css/bootstrap.min.css";
  import "bootstrap/dist/js/bootstrap.min.js";

  export default {
    name: "Header",
    data() {
      return {
        navList: [/*{
          name: "首 页",
          url: "/index"
        }, {
          name: "关于我们",
          url: "/about"
        }, {
          name: "产品展示",
          url: "/product",
          child: [{
            name: "产品分类一",
            url: "115.html",
          }, {
            name: "产品分类二",
            url: "74.html",
          }, {
            name: "产品分类三",
            url: "124.html",
          }]
        }, {
          name: "新闻资讯",
          url: "/news",
          child: [{
            name: "公司新闻",
            url: "86.html",
          }, {
            name: "行业新闻",
            url: "99.html",
          }, {
            name: "科技新闻",
            url: "106.html",
          }]
        }, {
          name: "下载中心",
          url: "/down"
        }, {
          name: "企业相册",
          url: "/photo"
        }, {
          name: "留言反馈",
          url: "/feedback"
        }, {
          name: "联系我们",
          url: "/contact"
        }*/]
      }
    },
    mounted() {
      if ($(window).width() > 768) {
        // 鼠标划过就展开子菜单
        $("ul.nav li.dropdown").hover(function () {
          $(this).find(".dropdown-menu").stop(true, true).slideDown();
        }, function () {
          $(this).find(".dropdown-menu").stop(true, true).slideUp();
        });
      }

      // scrollTop
      $(window).scroll(function () {
        let scrolls = $(window).scrollTop()
        if (scrolls > 10) {
          $(".navbar").addClass("small-nav");
          $(".flash").addClass("toflash");
        } else {
          $(".navbar").removeClass("small-nav");
          $(".flash").removeClass("toflash");
        }
      });
    }
  }
</script>

<style scoped>
  /*导航菜单*/
  .navbar {
    margin: 0px;
    background-color: #DA2625;
    border: none;
    /*margin-top: 35px;*/
    box-shadow: 0px 3px 4px rgba(0, 0, 0, 0.1);
  }

  #app_menudown {
    position: absolute;
    top: 0px;
    right: 0px;
    font-size: 16px;
    height: 40px;
  }

  #app_menudown:hover {
    background-color: #DA2625;
  }

  /*大屏幕*/
  @media screen and (min-width: 769px) {
    .logo {
      max-height: 76px;
      max-width: 346px;
      margin-top: 35px;
    }

    .navbar {
      min-height: 95px;
    }

    .navbar-nav {
      float: right;
    }

    .navbar-nav > li > a {
      text-align: center;
    }

    .navbar-default .navbar-nav > li > a {
      padding: 42px 13px 42px 13px;
      color: #fff;
      text-transform: uppercase;
      transition: 0.1s;
    }

    .navbar-default .navbar-nav > li > a:hover,
    .navbar-default .navbar-nav > li > a:focus,
    .navbar-default .navbar-nav > li > a.active,
    .navbar-default .navbar-nav > .active > a,
    .navbar-default .navbar-nav > .active > a:hover,
    .navbar-default .navbar-nav > .open > a,
    .navbar-default .navbar-nav > .open > a:hover,
    .navbar-default .navbar-nav > .open > a:focus {
      background-color: #A30100;
      color: #fff;
    }

    .navbar-default .navbar-nav-c > li > a {
      font-size: 16px;
      padding: 42px 16px 42px 16px;
    }

    .small-nav {
      min-height: 60px;
      margin-top: 0px;
      border-bottom: 1px solid #F3F3F3;
    }

    .small-nav .navbar-nav > li > a {
      padding-top: 20px;
      padding-bottom: 20px;
    }

    .small-nav img.logo {
      max-height: 50px;
      margin-top: 20px;
      max-width: 200px;
    }

    .nav_small {
      background-color: #fff;
      padding: 10px 0px 10px 0px;
      border: none;
      box-shadow: none;
      border-radius: 0px;
      font-size: 12px;
      min-width: 135px;
    }

    .nav_small > li {
      text-align: center;
    }

    .nav_small > li > a {
      line-height: 28px;
      color: #5e5e5e;
      padding-left: 28px;
      padding-right: 28px;
    }

    .nav_small > li > a:hover {
      color: #fff;
      background-color: #DA2625;
    }

    #app_menudown, #small_search {
      display: none;
    }

    .index_left_nav, .footer_nav {
      display: none;
    }
  }

  /*小屏幕*/
  @media screen and (max-width: 768px) {
    .navbar {
    }

    .navbar-default .navbar-brand {
      color: #fff;
    }

    .navbar-default .navbar-brand:hover,
    .navbar-default .navbar-brand:focus {
      color: #fff;
    }

    .navbar-toggle {
      border-color: #ccc;
    }

    .navbar-default .navbar-collapse, .navbar-default .navbar-form {
      border: 1px solid #ddd;
    }

    .navbar-default .navbar-toggle:hover,
    .navbar-default .navbar-toggle:focus {
      background: none;
    }

    .navbar-default .navbar-toggle .icon-bar {
      background-color: #ccc;
    }

    .navbar-default .navbar-nav {
      margin-top: 0px;
      margin-bottom: 0px;
    }

    .navbar-default .navbar-nav > li {
    }

    .navbar-default .navbar-nav > li:last-child {
      border: none;
    }

    .navbar-default .navbar-nav > li > a,
    .navbar-default .navbar-nav .open .dropdown-menu > li > a {
      color: #fff;
    }

    .navbar-default .navbar-nav > li > a:hover,
    .navbar-default .navbar-nav > li > a:focus,
    .navbar-default .navbar-nav > .active > a,
    .navbar-default .navbar-nav > .active > a:hover,
    .navbar-default .navbar-nav > .active > a:focus,
    .navbar-default .navbar-nav > .open > a,
    .navbar-default .navbar-nav > .open > a:hover,
    .navbar-default .navbar-nav > .open > a:focus,
    .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover {
      background-color: #DA2625;
      color: #fff;
    }

    .small-nav {
      margin-top: 0px;
      border-bottom: 1px solid #F3F3F3;
    }

    #gd {
      width: 70%;
    }

    .about_serv {
      background-position: right center;
      background-image: none;
      text-align: center;
      margin-top: 30px;
      margin-bottom: 10px;
    }

    .about_right {
      padding: 10px;
      padding-top: 60px;
    }

    .about_right .about_contents {
      padding: 10px;
    }

    .news_listd {
      margin-top: 30px;
    }

    .news_img {
      display: none;
    }

    .flash {
      margin-top: 50px;
    }

    .top_name {
      display: none;
    }

    .language {
      padding: 2px 0px 0px 0px;
    }

    .logo {
      margin: 15px 0px 0px 10px;
      max-width: 200px;
      max-height: 40px;
    }

    #topsearch {
      display: none;
    }

    .product_head h2 {
      font-size: 26px;
      margin-top: 28px;
    }

    .product_index {
      margin-top: 10px;
    }

    .product_list {
      padding: 20px 0px 0px 0px;
    }

    .product_img {
      min-height: auto;
      margin-bottom: 10px;
    }

    .product_list2 div.product_img {
      min-height: 80px;
      margin-bottom: 15px;
    }

    .process {
      padding-bottom: 25px;
    }

    .process_head p {
      text-align: center;
      padding: 20px 0px 0px 0px;
      margin: 0px;
    }

    .process_head h2 {
      text-align: center;
      padding: 10px 0px 0px 0px;
    }

    .process_col {
      margin-top: 28px;
    }

    .about_head {
      text-align: center;
    }

    .about_head h2 {
      margin: 0px 0px 6px 0px;
    }

    .about_head span {
      background-position: center;
    }

    .about_content {
      margin-top: 13px;
    }

    .about_img {
      width: 100%;
      clear: both;
      margin: 0px auto;
      margin-top: 20px;
    }

    a.about_btn {
      width: 160px;
      display: block;
      margin: 20px auto;
    }

    .news_head {
      margin: 0px 0px 20px 0px;
    }

    .news_headbg {
      width: 100%;
    }

    .news_head p {
      text-align: center;
      padding: 28px 0px 0px 0px;
    }

    .news_head h2 {
      text-align: center;
      padding: 7px 0px 7px 0px;
    }

    .news_head span {
      background-position: center;
      margin: 0px;
    }

    .news_index li {
      padding: 20px 0px 35px 0px;
    }

    .news_index li em {
      display: block;
    }

    .list_box {
      margin-top: 50px;
    }

    .page_bg {
      display: none;
    }

    .list_related h2.left_h {
      margin-top: 60px;
    }

    .product_con img, .contents img {
      width: 100%;
    }

    .news_time {
      display: none;
    }

    #pic-page a img {
      width: 35px;
    }

    #cmsFloatPanel {
      display: none;
    }

    .point span.to_prev, .point span.to_next {
      text-align: left;
      padding-bottom: 8px;
    }

    .product_list2 {
      padding-top: 25px;
    }

    .link_box {
      padding-left: 7px;
    }

    .link_box a {
      display: block;
      border-right: 0px;
      padding: 4px 0px;
    }

    .link_title {
      display: block;
    }

    .link_title:after {
      content: "";
    }

    .link_box button {
      display: inline-block;
      background-color: transparent;
      border: none;
      float: right;
      margin-top: -20px;
    }

    .link_box button:hover, .link_box button:focus {
      color: #99A1C5;
    }

    .link_list {
      display: none;
      padding-top: 7px;
    }

    .tags_box {
      padding-left: 7px;
    }

    .tags_box a {
      display: block;
      border-right: 0px;
      padding: 4px 0px;
    }

    .tags_title {
      display: block;
    }

    .tags_title:after {
      content: "";
    }

    .tags_box button {
      display: inline-block;
      background-color: transparent;
      border: none;
      float: right;
      margin-top: -20px;
    }

    .tags_box button:hover, .tags_box button:focus {
      color: #99A1C5;
    }

    .tags_rows {
      display: none;
      padding-top: 7px;
    }

    .footer_nav {
      background-color: #fafafa;
    }

    footer {
      margin-bottom: 50px;
      padding-left: 8px;
      padding-right: 8px;
    }

    .product_img > a {
      display: block;
      padding-top: 100%;
      position: relative;
    }

    .product_img a img {
      position: absolute;
      top: 0;
      left: 0;
      height: 99.8%;
    }

  }
</style>
