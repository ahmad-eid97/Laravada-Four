<template>
  <div class="home">
    <app-home-intro :bannerHead="bannerHead"></app-home-intro>
    <app-home-partners :partners="partners"></app-home-partners>
    <app-home-features :features="features"></app-home-features>
    <app-home-solutions :solutions="solutions"></app-home-solutions>
    <app-home-banner :latestBlog="latestBlog"></app-home-banner>
    <app-home-sections :services="services"></app-home-sections>
    <app-home-bottom-banner
      :bottomBanner="bottomBanner"
    ></app-home-bottom-banner>
  </div>
</template>

<script>
import AppHomeBanner from "../components/home/AppHomeBanner.vue";
import AppHomeIntro from "../components/home/AppHomeIntro.vue";
import AppHomePartners from "../components/home/AppHomePartners.vue";
import AppHomeFeatures from "../components/home/AppHomeFeatures.vue";
import AppHomeSolutions from "../components/home/AppHomeSolutions.vue";
import AppHomeSections from "../components/home/AppHomeSections.vue";
import AppHomeBottomBanner from "../components/home/AppHomeBottomBanner.vue";

export default {
  name: "Home",
  async asyncData({ $axios, app }) {
    const bannerHead = await $axios.get("/sections/banner", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    const partners = await $axios.get("/partners");

    const features = await $axios.get("/sections/features", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    const solutions = await $axios.get("/sections/solutions", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    const latestBlog = await $axios.get("/blogs?latest=1");

    const services = await $axios.get("/services");

    const bottomBanner = await $axios.get("/sections/banner-bottom", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    return {
      bannerHead: bannerHead.data.data,
      partners: partners.data.data.partners,
      features: features.data.data,
      solutions: solutions.data.data,
      latestBlog: latestBlog.data.data.blogs.slice(0, 1),
      services: services.data.data.services,
      bottomBanner: bottomBanner.data.data,
    };
  },
  components: {
    AppHomeIntro,
    AppHomePartners,
    AppHomeBanner,
    AppHomeFeatures,
    AppHomeSolutions,
    AppHomeSections,
    AppHomeBottomBanner,
  },
};
</script>
<style></style>
