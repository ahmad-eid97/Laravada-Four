<template>
  <div class="courseIntro">
    <div class="row align-items-center">
      <div class="col-lg-6">
        <img :src="courseDetails.image" alt="courseImage" />
      </div>
      <div class="col-lg-6">
        <div class="details">
          <div class="rate">
            <b-form-rating
              color="#f39c12"
              :inline="true"
              :no-border="true"
              value="5"
              readonly
            ></b-form-rating>
            <span>( 1 Customer Reviews )</span>
          </div>

          <h1>{{ courseDetails.title }}</h1>

          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus
            vel metus malesuada ante imperdiet lobortis.
          </p>

          <div class="price">
            <p class="pre">${{ courseDetails.previous_price }}</p>
            <p>${{ courseDetails.current_price }}</p>
          </div>

          <button>Add to cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["courseDetails"],
};
</script>

<style scoped lang="scss">
output {
  padding: 0;
}
.courseIntro {
  margin-top: 100px;
  img {
    @include md {
      margin-bottom: 30px;
    }
  }
  .details {
    h1 {
      margin-top: 20px;
    }
    p {
      font-size: 1.5rem;
      opacity: 0.8;
    }
    .price {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 20px;
      p {
        font-size: 1.5rem;
        opacity: 0.7;
        margin: 0;
        &:not(.pre) {
          color: var(--main-color);
          font-weight: bold;
        }
        &.pre {
          text-decoration: line-through;
        }
      }
    }
    button {
      padding: 10px 40px;
      font-size: 1.3rem;
      border: 1px solid var(--main-color);
      color: #fff;
      background-color: var(--main-color);
      &:hover {
        background-color: transparent;
        color: var(--main-color);
      }
    }
  }
}
</style>
