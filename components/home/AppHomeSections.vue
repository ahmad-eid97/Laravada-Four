<template>
  <div class="sections">
    <h1>Services We Provide</h1>

    <div class="row m-0">
      <div
        v-for="service in services.slice(0, 3)"
        :key="service.id"
        class="col-lg section"
        @click="$router.push(localePath(`/service/${service.id}`))"
      >
        <div class="heading text-center">
          <nuxt-link :to="localePath(`/service/${service.id}`)">
            <img class="img-fluid" :src="service.image" :alt="service.title" />
          </nuxt-link>
        </div>
        <p v-if="service.short_description">
          {{ service.short_description.substring(0, 200) + "..." }}
        </p>
      </div>
    </div>

    <div class="bottomButton" @click="$router.push('/services')">
      <button>See More</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppHomeSections",
  props: ["services"],
  data() {
    return {};
  },
};
</script>
<style lang="scss">
.sections {
  padding-bottom: 45px;
  padding-left: 30px;
  padding-right: 30px;
  padding-top: 45px;
}

.sections h1 {
  text-align: center;
  margin-bottom: 50px;
}

.sections p {
  color: rgb(118, 136, 148);
  font-family: Roboto;
  font-size: 22px;
  font-weight: 400;
  line-height: 34px;
  margin-bottom: 20px;
  padding-left: 50px;
  padding-right: 50px;
  text-align: center;
}
.bordered {
  border-right: 1px solid #ebebeb;
  border-left: 1px solid #ebebeb;
}
.heading img {
  width: 100%;
  height: 250px;
  margin-bottom: 30px;
  object-fit: contain;
}
.bottomButton {
  display: flex;
  justify-content: center;
  button {
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
    &:hover {
      background-color: var(--main-color);
    }
  }
}
@include xs {
  .heading img {
    width: 220px;
  }

  .sections p {
    font-size: 18px;
    line-height: 28px;
  }
}
</style>
