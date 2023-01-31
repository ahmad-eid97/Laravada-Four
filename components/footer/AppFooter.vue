<template>
  <footer>
    <subscribe />
    <b-navbar toggleable="lg">
      <b-navbar-brand href="#">
        <img
          :src="
            $store.state.websiteSettings.find((one) => one.key === 'logo')
              .plain_value
          "
          alt="logoImage"
        />
      </b-navbar-brand>

      <b-navbar-toggle target="navbar-toggle-collapse">
        <template #default="{ expanded }">
          <span
            class="menu-trigger"
            :class="expanded ? 'active' : ''"
            id="menu03"
          >
            <span></span>
            <span></span>
            <span></span>
          </span>
        </template>
      </b-navbar-toggle>

      <b-collapse
        id="navbar-toggle-collapse"
        class="ml-auto justify-content-end"
        is-nav
      >
        <b-navbar-nav class="align-items-center">
          <li v-for="page in $store.state.footerPages" :key="page.id">
            <b-nav-item
              :to="localePath(generatePagePath(page.id))"
              v-if="page.status"
              >{{ page.name }}</b-nav-item
            >
          </li>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <div class="row mx-0 justify-content-center">
      <div class="col-12 copyright">
        <p>
          © Copyright 2023&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;Laravada
          Theme&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;All Rights
          Reserved&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;Powered by
          <nuxt-link to="http://wordpress.org" target="_blank" rel="noreferrer"
            >Rail Coder</nuxt-link
          >
        </p>
      </div>
    </div>
  </footer>
</template>

<script>
import Subscribe from "../subscribe/subscribe.vue";
export default {
  name: "AppFooter",
  components: { Subscribe },
  data() {
    return {
      side: false,
    };
  },
  methods: {
    generatePagePath(id) {
      switch (id) {
        case 1:
          return "/about";
        case 2:
          return "/contact";
        case 3:
          return "/terms";
        case 4:
          return "/policy";
      }
    },
  },
  mounted() {},
};
</script>
<style>
footer {
  min-height: 60px;
  background-color: #fff;
  z-index: 9999;
}
footer .navbar {
  padding-bottom: 50px;
  padding-left: 60px;
  padding-right: 60px;
  padding-top: 50px;
}
.navbar-brand {
  padding-top: 0px !important;
  padding-right: 0px !important;
  margin-right: 25px;
  padding-bottom: 0px !important;
  padding-left: 0px !important;
}
.navbar-brand img {
  max-width: 162px;
  height: auto;
}
.nav-item {
  position: relative;
  margin: 0 20px;
  justify-content: center;
  transition: all calc(300 * 1ms) cubic-bezier(0.42, 0.01, 0.58, 1);
}
.nav-link {
  font-size: 22px;
  font-weight: 400;
  line-height: 30px;
  color: rgb(97, 106, 125);
}
.active .nav-link,
.nav-link:hover {
  color: rgb(98, 57, 189);
}

.navbar-toggler,
.navbar-toggler:focus {
  border: none;
  box-shadow: none;
}
.menu-trigger,
.menu-trigger span {
  display: inline-block;
  transition: all 0.4s;
  box-sizing: border-box;
}
.menu-trigger {
  position: relative;
  width: 32px;
  height: 25px;
  background: none;
  border: none;
  appearance: none;
  cursor: pointer;
}
.menu-trigger span {
  position: absolute;
  left: 0;
  width: 100%;
  height: 5px;
  background-color: rgb(98, 57, 189);
  border-radius: 4px;
}
.menu-trigger span:nth-of-type(1) {
  top: 0;
}
.menu-trigger span:nth-of-type(2) {
  top: 10px;
}
.menu-trigger span:nth-of-type(3) {
  bottom: 0;
}
#menu03.active {
  transform: rotate(360deg);
}
#menu03.active span:nth-of-type(1) {
  transform: translateY(10px) rotate(-45deg);
}
#menu03.active span:nth-of-type(2) {
  transform: translateY(0) rotate(45deg);
}
#menu03.active span:nth-of-type(3) {
  opacity: 0;
}

nav .btn {
  border-radius: 25px 25px 25px 25px;
  padding-bottom: 13px;
  padding-left: 29px;
  padding-right: 29px;
  padding-top: 13px;
  font-weight: 500;
  justify-content: center;
  letter-spacing: 0.21px;
  font-size: 14px;
  color: rgb(255, 255, 255);
  background-color: #74c5da;
  line-height: 17px;
  min-width: 200px;
  text-transform: uppercase;
  font-family: "Roboto";
  border: none;
}
nav .btn:hover {
  border-radius: 25px 25px 25px 25px;
  padding-bottom: 13px;
  padding-left: 29px;
  padding-right: 29px;
  padding-top: 13px;
  font-weight: 500;
  justify-content: center;
  letter-spacing: 0.21px;
  font-size: 14px;
  color: rgb(255, 255, 255);
  background-color: var(--main-color);
  line-height: 17px;
  min-width: 200px;
  text-transform: uppercase;
  font-family: "Roboto";
  border: none;
}
.side-bar {
  width: 0;
  position: fixed;
  overflow: hidden;
  top: 0;
  bottom: 0;
  right: 0;
  background-color: rgba(243, 245, 246, 0.95);
  z-index: 9999;
  transition: all 0.4s ease;
}
.side-bar.opend {
  width: 300px;
}
.side-bar .content-wrapper {
  padding: 60px 30px;
  position: relative;
  overflow-x: hidden;
  overflow-y: auto;
  height: 100%;
  scrollbar-width: none;
}
.side-bar .content-wrapper .close-btn {
  position: absolute;
  top: 20px;
  right: auto;
  left: 20px;
  color: rgb(97, 106, 125);
  font-size: 20px;
  cursor: pointer;
}
.side-bar .content-wrapper .widget {
  margin-bottom: 50px;
}
.side-bar .content-wrapper h4 {
  font-family: Roboto;
  font-size: 18px;
  font-weight: 400;
  letter-spacing: 1px;
  line-height: 18px;
  margin-bottom: 28px;
  color: rgb(9, 41, 51);
}
.side-bar .content-wrapper p {
  color: rgb(97, 106, 125);
  font-family: Roboto;
  font-size: 15px;
  font-weight: 400;
  line-height: 30px;
  margin: 15px 0;
}
.side-bar .content-wrapper ul {
  list-style: none;
  padding: 0;
}
.side-bar .content-wrapper ul li {
  color: rgb(97, 106, 125);
  align-items: start;
  display: flex;
}
.side-bar .content-wrapper ul li > div {
  display: inline-block;
}
.side-bar .content-wrapper ul li > div p {
  margin: -4px 0 0 12px;
}
@media screen and (max-width: 991px) {
  .navbar-collapse.show {
    position: absolute;
    left: 0;
    right: 0;
    z-index: 9999;
    top: 120%;
  }
  .nav-item {
    width: 100%;
    border-bottom: 1px solid #e5e5e5;
    background: #fff;
  }

  .nav-item.active,
  .nav-item:hover {
    background-color: rgb(98, 57, 189);
  }
  .nav-item.active .nav-link,
  .nav-item:hover .nav-link {
    color: #fff;
  }

  .nav-link {
    padding: 16px 30px !important;
    font-weight: 400;
    font-size: 23px;
    text-align: left;
    color: rgb(97, 106, 125);
  }
  .side-bar.opend {
    width: 100%;
  }
}
.copyright {
  min-height: 60px;
  padding-bottom: 30px;
  padding-left: 60px;
  padding-right: 60px;
  padding-top: 30px;
  background-color: rgb(244, 246, 247);
}
.copyright p {
  color: rgb(118, 136, 148);
  font-family: Roboto;
  font-size: 13px;
  font-weight: 400;
  line-height: 30px;
}
.copyright p a {
  color: rgb(98, 57, 189);
  text-decoration: none;
}
</style>
