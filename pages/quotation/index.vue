<template>
  <div class="quotation">
    <quotation-heading />
    <div class="container">
      <div class="quotationWrapper">
        <h1>hello sir</h1>
      </div>
    </div>
  </div>
</template>

<script>
import quotationHeading from "../../components/quotation/quotationHeading.vue";

export default {
  components: {
    quotationHeading,
  },
};
</script>

<style scoped lang="scss">
.quotationWrapper {
  margin-top: 100px;
}
</style>
