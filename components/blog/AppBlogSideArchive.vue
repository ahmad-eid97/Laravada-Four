<template>
  <div class="side-bar-widget">
    <h3 class="title">Blog Categories</h3>
    <div
      class="side-bar-categories"
      v-if="blogDetails && blogDetails.features.length >= 1"
    >
      <ul>
        <li v-for="feature in blogDetails.features" :key="feature">
          <i class="fa-solid fa-circle-dot"></i>
          <nuxt-link to="#" target="_blank">{{ feature }}</nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppBlogSideArchive",
  props: ["blogDetails"],
};
</script>

<style>
.side-bar-widget .title {
  font-size: 20px;
  color: #212529;
  padding: 0;
  font-weight: 600;
  position: relative;
  display: inline-block;
  margin-bottom: 10px;
  background-color: transparent;
  width: 100%;
}
.side-bar-widget .side-bar-categories {
  margin-bottom: 15px;
}
.side-bar-widget .side-bar-categories ul {
  padding: 0;
  margin: 0;
  list-style-type: none;
}
.side-bar-widget .side-bar-categories ul li {
  position: relative;
  font-size: 15px;
  font-weight: 500;
}
.side-bar-widget .side-bar-categories ul li .line-circle {
  position: absolute;
  top: 10px;
  left: 0;
  width: 13px;
  height: 13px;
  background-color: transparent;
  border: 1px solid var(--main-color);
  border-radius: 50px;
}
.side-bar-widget .side-bar-categories ul li .line-circle::before {
  content: "";
  position: absolute;
  top: 1px;
  left: 1px;
  right: 1px;
  margin: 0 auto;
  width: 9px;
  height: 9px;
  background-color: var(--main-color);
  border-radius: 50px;
}
.side-bar-widget .side-bar-categories ul li a {
  display: inline-block;
  color: #444;
  font-weight: 400;
  padding: 5px 0;
  font-weight: 600;
  position: relative;
  width: 100%;
}
.side-bar-widget .side-bar-categories ul li a:hover {
  color: var(--main-color);
}
.side-bar-widget .side-bar-categories ul li a span {
  right: 30px;
  position: absolute;
  top: 10px;
  color: #444;
}
</style>
