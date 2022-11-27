<template>
  <div class="home">
    <app-home-intro></app-home-intro>
    <app-home-partners></app-home-partners>
    <app-home-features></app-home-features>
    <app-home-solutions></app-home-solutions>
    <app-home-banner></app-home-banner>
    <app-home-sections></app-home-sections>
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
  components: {
    AppHomeIntro,
    AppHomePartners,
    AppHomeBanner,
    AppHomeFeatures,
    AppHomeSolutions,
    AppHomeSections,
    AppHomeBottomBanner
  },
  mounted() {
    console.log('==================>', this.$store.state.websiteSettings)
  }
}
</script>
<style>
  
</style>
