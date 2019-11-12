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
            <img src="../assets/logo.jpg" class="logo" alt="企业通用模版网站"/>
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
    data() {
      return {
        navList: [{
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
        }]
      }
    },
    mounted() {
      if ($(window).width() > 768) {
        //鼠标划过就展开子菜单
        $("ul.nav li.dropdown").hover(function () {
          $(this).find(".dropdown-menu").stop(true, true).slideDown();
        }, function () {
          $(this).find(".dropdown-menu").stop(true, true).slideUp();
        });
      }
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
</style>
