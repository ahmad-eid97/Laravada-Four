<template>
  <section class="intro">
    <!-- <VueSlickCarousel :arrows="true" :fade="true" :dots="false"> -->
    <div class="item item-1">
      <div class="row h-100 m-0 align-items-start">
        <div class="col-md-6">
          <h1>
            {{ bannerHead.find((one) => one.key === "banner_title").value }}
          </h1>
          <a
            :href="bannerHead.find((one) => one.key === 'banner_link').value"
            class="btn"
            ><i class="fa-brands fa-mixcloud mx-2"></i> Explore solutions</a
          >
        </div>
        <div class="col-md-6">
          <img
            class="img-fluid"
            :src="bannerHead.find((one) => one.key === 'banner_image').value"
            alt=""
          />
        </div>
      </div>
    </div>
    <!-- </VueSlickCarousel> -->
  </section>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
import "animate.css/animate.css";
export default {
  name: "AppHomeIntro",
  props: ["bannerHead"],
  components: {
    VueSlickCarousel,
  },
  data() {
    return {};
  },
};
</script>
<style lang="scss">
.intro .item-1 {
  background-color: rgba(255, 255, 255, 0);
  background-image: url("https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/11/avada-it-clouds1.png");
  background-position: center center;
  background-repeat: no-repeat;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
}
.intro .item .row {
  padding-top: 7vw;
  padding-right: 30px;
  padding-bottom: 8vw;
  padding-left: 30px;
  min-height: calc(100vh - 110px);
}
.intro .item h1 {
  color: #fff;
  font-size: 120px;
  font-weight: 400;
  line-height: 114px;
  padding-top: 70px;
}

@include xs {
  .intro .item h1 {
    font-size: 60px;
    line-height: 80px;
  }
}

.intro .item p {
  font-size: 20px;
  color: #fff;
  font-weight: 400;
}

.slick-prev::before,
.slick-next::before {
  font-family: "slick";
  font-size: 20px;
  line-height: 1;
  opacity: 0.75;
  color: #fff;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #000;
  padding: 10px;
}
.item .btn {
  border-radius: 25px 25px 25px 25px;
  padding-bottom: 17px;
  padding-left: 40px;
  padding-right: 40px;
  padding-top: 17px;
  font-weight: 500;
  justify-content: center;
  letter-spacing: 2px;
  font-size: 18px;
  color: rgb(255, 255, 255);
  background-color: #74c5da;
  line-height: 17px;
  min-width: 200px;
  text-transform: uppercase;
  font-family: "Roboto";
  border: none;
}
.item .btn:hover {
  justify-content: center;
  color: rgb(255, 255, 255);
  background-color: var(--main-color);
  border: none;
}

.slick-active .item h1 {
  animation: fadeInLeft;
  animation-duration: 2s;
}
.slick-active .item p {
  animation: fadeInLeft;
  animation-duration: 3s;
}
.slick-active .item .btn {
  animation: fadeInUp;
  animation-duration: 4s;
}
.slick-active .item .btn.blue {
  animation: fadeInUp;
  animation-duration: 5s;
}
.slick-active .item img {
  animation: fadeIn;
  animation-duration: 5s;
}
</style>
