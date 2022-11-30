<template>
  <div class="home">
    <app-home-intro></app-home-intro>
    <app-home-partners :partners="partners"></app-home-partners>
    <app-home-features :features="features"></app-home-features>
    <app-home-solutions :solutions="solutions"></app-home-solutions>
    <app-home-banner :latestBlog="latestBlog"></app-home-banner>
    <app-home-sections :services="services"></app-home-sections>
    <app-home-bottom-banner></app-home-bottom-banner>
  </div>
</template>

<script>
import AppHomeBanner from '../components/home/AppHomeBanner.vue'
import AppHomeIntro from '../components/home/AppHomeIntro.vue'
import AppHomePartners from '../components/home/AppHomePartners.vue'
import AppHomeFeatures from '../components/home/AppHomeFeatures.vue'
import AppHomeSolutions from '../components/home/AppHomeSolutions.vue'
import AppHomeSections from '../components/home/AppHomeSections.vue'
import AppHomeBottomBanner from '../components/home/AppHomeBottomBanner.vue'

export default {
  name: 'Home',
  async asyncData({ $axios }) {
    const partners = await $axios.get('/partners');

    const features = await $axios.get('/sections/features');

    const solutions = await $axios.get('/sections/solutions');

    const latestBlog = await $axios.get('/blogs?latest=1');

    const services = await $axios.get('/services');

    return {
      partners: partners.data.data.partners,
      features: features.data.data,
      solutions: solutions.data.data,
      latestBlog: latestBlog.data.data.blogs.slice(0, 1),
      services: services.data.data.services,
    }
  },
  components: {
    AppHomeIntro,
    AppHomePartners,
    AppHomeBanner,
    AppHomeFeatures,
    AppHomeSolutions,
    AppHomeSections,
    AppHomeBottomBanner
  },
}
</script>
<style>
  
</style>
