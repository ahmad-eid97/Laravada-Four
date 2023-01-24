<template>
  <div class="home">
    <app-home-intro :slides="slides"></app-home-intro>
    <app-home-partners :partners="partners"></app-home-partners>
    <app-home-features :features="features"></app-home-features>
    <app-home-activities :activities="activities" />
    <app-home-steps :steps="steps" />
    <app-home-solutions :solutions="solutions"></app-home-solutions>
    <app-home-banner :latestBlog="latestBlog"></app-home-banner>
    <app-home-sections :services="services"></app-home-sections>
    <app-home-bottom-banner
      :bottomBanner="bottomBanner"
    ></app-home-bottom-banner>
    <SocialChat :attendants="attendants">
      <p slot="header">Click one of our representatives below to chat.</p>
      <template v-slot:button="{ open }">
        <span v-show="!open">Contact us</span>
        <span v-show="open">Close</span>
      </template>
      <small slot="footer">Opening hours: 8am to 10pm</small>
    </SocialChat>
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
import AppHomeActivities from "../components/home/AppHomeActivities.vue";
import AppHomeSteps from "../components/home/AppHomeSteps.vue";

export default {
  name: "Home",
  data() {
    return {
      attendants: [
        {
          app: "whatsapp",
          label: "Support",

          name: this.$store.state.websiteSettings.find(
            (one) => one.key === "chat_widget_whatsapp_label"
          )
            ? this.$store.state.websiteSettings.find(
                (one) => one.key === "chat_widget_whatsapp_label"
              ).plain_value
            : "Laravada",

          number: this.$store.state.websiteSettings.find(
            (one) => one.key === "chat_widget_whatsapp_number"
          )
            ? this.$store.state.websiteSettings.find(
                (one) => one.key === "chat_widget_whatsapp_number"
              ).plain_value
            : "11111111111",

          avatar: {
            src: "https://avatars0.githubusercontent.com/u/8084606?s=460&u=20b6499a416cf7129a18e5c168cf387e159edb1a&v=4",
            alt: "Laravada customer support",
          },
        },
        {
          app: "messenger",
          label: "Technical support",

          name: this.$store.state.websiteSettings.find(
            (one) => one.key === "chat_widget_messenger_label"
          )
            ? this.$store.state.websiteSettings.find(
                (one) => one.key === "chat_widget_messenger_label"
              ).plain_value
            : "Laravada Facebook",

          id: this.$store.state.websiteSettings.find(
            (one) => one.key === "chat_widget_messenger_id"
          )
            ? this.$store.state.websiteSettings.find(
                (one) => one.key === "chat_widget_messenger_id"
              ).plain_value
            : "111111111111",

          avatar: {
            src: "https://avatars0.githubusercontent.com/u/8084606?s=460&u=20b6499a416cf7129a18e5c168cf387e159edb1a&v=4",
            alt: "Laravada customer support",
          },
        },
      ],
    };
  },
  async asyncData({ $axios, app }) {
    const slides = await $axios.get("/sliders", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

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

    const activities = await $axios.get("/sections/activities", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    const steps = await $axios.get("/sections/steps", {
      headers: {
        "Accept-Language": app.i18n.locale,
      },
    });

    return {
      slides: slides.data.data.sliders,
      bannerHead: bannerHead.data.data,
      partners: partners.data.data.partners,
      features: features.data.data,
      solutions: solutions.data.data,
      latestBlog: latestBlog.data.data.blogs.slice(0, 1),
      services: services.data.data.services,
      bottomBanner: bottomBanner.data.data,
      activities: activities.data.data,
      steps: steps.data.data,
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
    AppHomeActivities,
    AppHomeSteps,
  },
};
</script>
<style>
.home {
  --vsc-bg-header: var(--main-color);
  --vsc-bg-footer: var(--main-color);
  --vsc-text-color-header: #fff;
  --vsc-text-color-footer: #fff;
  --vsc-bg-button: var(--main-color);
  --vsc-text-color-button: #fff;
  --vsc-outline-color: var(--main-color);
  --vsc-border-color-bottom-header: #fff;
  --vsc-border-color-top-footer: #fff;
}
</style>
