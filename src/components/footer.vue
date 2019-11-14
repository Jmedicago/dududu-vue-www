<template>
  <footer>
    <div class="copyright">
      <p>
        CopyRight 2019 All Right Reserved Vue {{name}}<br>网站ICP:{{icp}}
        <a href="#" target="_blank">网站地图</a>
      </p>
      <p class="copyright_p">
        地址：{{address}} &nbsp;电话：{{phone}} &nbsp;邮箱：{{email}}&nbsp;
      </p>
    </div>
  </footer>
</template>

<script>
  export default {
    name: "Footer",
    data() {
      return {
        name: "嘟嘟嘟网络科技",
        icp: "000000",
        address: "黄冈市黄州沿江大道13号江山如画3幢1单元604",
        phone: "13409811204",
        email: "wenjf1996@aliyun.com",
      }
    }
  }
</script>

<style scoped>
  /*底部信息*/
  footer {
    text-align: center;
    background-color: #A30100;
    color: #fff;
    padding: 30px 0px 20px 0px;
    font-size: 12px;
  }

  .copyright {
    line-height: 20px;
  }

  .copyright a {
    color: #fff;
  }

  .foot_nav {
    width: 25%;
    float: left;
    background-color: #fafafa;
    text-align: center;
    color: #898989;
    cursor: pointer;
  }

  .foot_nav:hover, .foot_nav:focus {
    background-color: #e4e4e4;
    cursor: pointer;
  }

  .foot_nav a {
    color: #898989;
    display: block;
  }

  .foot_nav a:hover, .foot_nav a:focus {
    text-decoration: none;
  }

  .foot_nav span {
    display: block;
    padding: 3px 0px 0px 0px;
  }

  /*小屏幕*/
  @media screen and (max-width: 768px) {
    .footer_nav {
      background-color: #fafafa;
    }

    footer {
      margin-bottom: 50px;
      padding-left: 8px;
      padding-right: 8px;
    }
  }

  @media screen and (max-width: 767px) {
    .copyright_p {
      display: none;
    }
  }

</style>
