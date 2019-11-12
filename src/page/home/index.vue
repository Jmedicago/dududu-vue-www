<template>
  <div>
    <Header></Header>
    <!-- slider -->
    <div class="flash">
      <ul class="bxslider">
        <li>
          <a href="http://">
            <img src="../../assets/1556441135.jpg" alt="广告标题"/>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import "bootstrap/dist/css/bootstrap.min.css";
  import "bootstrap/dist/js/bootstrap.min.js";
  import Header from "../../components/header";


  export default {
    components: {Header}
  }
</script>

<style scoped>
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
</style>
