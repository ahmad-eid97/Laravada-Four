<template>
  <div class="jobsListed">
    <h6>Trending Jobs</h6>
    <h1>All Popular Listed jobs</h1>

    <div class="row justify-content-center">
      <div
        v-for="job in jobsList"
        :key="job"
        class="col-md-6 col-lg-4 col-xl-3 mb-4"
      >
        <div class="job" @click="$router.push(localePath(`/career/${job.id}`))">
          <span
            v-if="job.category"
            class="category"
            :style="{ backgroundColor: random_rgba() }"
            >{{ job.category.name }}</span
          >
          <img v-if="job.photo" :src="job.photo" alt="jobImage" />
          <h3>{{ job.title }}</h3>
          <div class="tags" v-if="job.skills">
            <span
              v-for="skill in job.skills.split('\r\n').slice(0, 6)"
              :key="skill"
              >{{ skill }}</span
            >
          </div>
        </div>
      </div>

      <div class="btn">
        <button>Explore More Jobs</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["jobsList"],
  data() {
    return {};
  },
  methods: {
    random_rgba() {
      var o = Math.round,
        r = Math.random,
        s = 255;
      return (
        "rgba(" +
        o(r() * s) +
        "," +
        o(r() * s) +
        "," +
        o(r() * s) +
        "," +
        "0.2" +
        ")"
      );
    },
  },
};
</script>

<style scoped lang="scss">
.jobsListed {
  margin-top: 100px;
  h6,
  h1 {
    text-align: center;
  }
  h1 {
    margin-bottom: 50px;
  }
  .job {
    border: 1px solid #e5e6e7;
    padding: 40px 20px 20px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: relative;
    margin-bottom: 20px;
    height: 100%;
    .category {
      position: absolute;
      top: 10px;
      right: 10px;
      padding: 0px 10px;
      border-radius: 5px;
    }
    img {
      width: 100px;
      margin-bottom: 10px;
      cursor: pointer;
    }
    h3 {
      cursor: pointer;
    }
    .tags {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 10px;
      span {
        background: #f1f3f5;
        padding: 5px 10px;
        border-radius: 5px;
        font-size: 1rem;
      }
    }
  }
  .btn {
    display: grid;
    place-content: center;
    border: none;
    button {
      background-color: var(--main-color);
      color: #fff;
      padding: 10px 30px;
      border: 1px solid var(--main-color);
      border-radius: 20px;
      outline: none;
      &:hover {
        background-color: transparent;
        color: var(--main-color);
      }
    }
  }
}
</style>
