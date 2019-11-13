<template>
  <div class="link_box">
    <div class="container">
      <span class="link_title">友情链接</span>
      <button id="link_btn" class="glyphicon glyphicon-plus" aria-hidden="true"></button>
      <span class="link_list">
          <a :href="item.url" target="_self" v-for="item in linkList">{{item.title}}</a>
      </span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Link",
    data() {
      return {
        linkList: [{
          url: "https://vuejs.org/",
          title: "Vue"
        }, {
          url: "https://www.java.com",
          title: "Java"
        }, {
          url: "https://github.com/",
          title: "Github"
        }]
      }
    }
  }
</script>

<style scoped>
  /*友情链接*/
  .link_box {
    background-color: #DA2625;
    padding: 10px 0px;
    text-align: center;
    color: #fff;
    font-size: 13px;
    margin-top: 25px;
  }

  .link_box a {
    color: #fff;
    border-right: 1px solid #fff;
    padding: 0px 10px 0px 10px;
    font-size: 13px;
  }

  .link_box a:hover {
    text-decoration: none;
    color: #FBF9B0;
  }

  .link_box a:last-child {
    border-right: 0px;
  }

  .link_box button {
    display: none;
  }

  .link_title {
    font-size: 13px;
    margin-right: -6px;
  }

  .link_title:after {
    content: "：";
  }

  #link_btn:hover, #link_btn:focus {
    color: #FDFB98;
  }
</style>
