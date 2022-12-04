<template>
  <div class="banner">
    <div class="row m-0 justify-content-between">
      <div class="col-lg-auto">
        <div class="title">
          <h2>LATEST INSIGHT <span>.</span></h2>
          <div class="seprator"></div>
        </div>
      </div>
      <div class="col-lg-8">
        <div class="content">
          <h2>{{ latestBlog[0].title }}</h2>
          <p>
            {{ latestBlog.short_description }}
          </p>
          <div class="btn-container d-flex justify-content-end">
            <nuxt-link :to="`/blog/${latestBlog[0].id}`"
              >Read More <i class="fa-solid fa-angle-right"></i
            ></nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppHomeBanner",
  props: ["latestBlog"],
  data() {
    return {};
  },
};
</script>
<style>
.banner {
  background-color: rgb(118, 136, 148);
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  background-image: url("https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/avad-it-home-article.jpg");
  padding-top: 100px;
  padding-right: 30px;
  padding-bottom: 110px;
  padding-left: 30px;
}
.banner .title {
  margin-top: 85px;
}
.banner .title h2 {
  color: rgb(255, 255, 255);
  font-family: Teko;
  font-size: 65px;
  font-weight: 400;
  line-height: 65px;
  text-align: left;
  text-transform: uppercase;
  max-width: 250px;
}

.banner .title h2 span {
  color: rgb(116, 197, 218);
}

.banner .seprator {
  width: 100px;
  margin-bottom: 50px;
  background-color: rgb(116, 197, 218);
  height: 4px;
}
.banner .content {
  background-color: rgba(255, 255, 255, 0.8);
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-left: 50px;
  padding-right: 50px;
  padding-top: 50px;
}
.banner .content h2 {
  color: rgb(98, 57, 189);
  font-family: Teko;
  font-size: 42px;
  font-weight: 400;
  margin-bottom: 25px;
}
.banner .content p {
  color: rgb(118, 136, 148);
  font-family: Roboto;
  font-size: 16px;
  font-weight: 400;
  line-height: 30px;
  margin-bottom: 20px;
}
.banner .content .btn-container {
  border-bottom: 1px solid rgb(98, 57, 189);
  border-top: 1px solid rgb(98, 57, 189);
  padding-bottom: 5px;
  padding-top: 5px;
  margin-bottom: 65px;
}
.banner .content .btn-container a {
  color: rgb(98, 57, 189);
  font-family: Roboto;
  font-size: 13px;
  font-weight: 400;
  line-height: 30px;
  margin-right: 10px;
  text-align: right;
  text-decoration-line: none;
}
</style>
