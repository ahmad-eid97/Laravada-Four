<template>
  <section class="solutions">
    <div class="row align-items-center">
      <div class="col-lg-6 mb-5">
        <h2 class="heading">
          {{ solutions.find((one) => one.key === "solutions_title").value
          }}<span>.</span>
        </h2>
        <div class="seprator"></div>
        <p>
          {{
            solutions.find((one) => one.key === "solutions_description").value
          }}
        </p>
        <div
          class="row m-0"
          v-if="solutions.find((one) => one.key === 'solutions_list').value"
        >
          <div
            v-for="item in solutions.find((one) => one.key === 'solutions_list')
              .value"
            :key="item"
            class="col-sm-6 solution"
          >
            <h2>
              <span class="icon"><i :class="item.icon"></i></span>
              <span>{{ item.title }}</span>
            </h2>
            <p>
              {{ item.description }}
            </p>
          </div>
        </div>
        <a
          :href="solutions.find((one) => one.key === 'solutions_link').value"
          class="btn"
          >Our solutions</a
        >
      </div>
      <div class="col image text-center">
        <img
          class="img-fluid"
          :src="solutions.find((one) => one.key === 'solutions_image').value"
          alt="solutions image"
        />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AppHomeSolutions",
  props: ["solutions"],
  data() {
    return {};
  },
  mounted() {
    document
      .querySelector(".solutions")
      .style.setProperty(
        "--solutions-bg",
        this.solutions.find(
          (one) => one.key === "solutions_background_active_section"
        ).value === "color"
          ? this.solutions.find(
              (one) => one.key === "solutions_background_color_section"
            ).value
          : `url(${
              this.solutions.find(
                (one) => one.key === "solutions_background_image_section"
              ).value
            })`
      );

    document
      .querySelector(".solutions")
      .style.setProperty(
        "--solutions-fontSize",
        `${
          this.solutions.find(
            (one) => one.key === "solutions_font_size_section"
          ).value
        }px`
      );

    if (
      this.solutions.find(
        (one) => one.key === "solutions_border_position_section"
      ) &&
      this.solutions.find(
        (one) => one.key === "solutions_border_position_section"
      ).value === "both"
    ) {
      document
        .querySelector(".solutions")
        .style.setProperty(
          "--solutions-border-top",
          `${
            this.solutions.find(
              (one) => one.key === "solutions_border_size_section"
            ).value
          }px ${
            this.solutions.find(
              (one) => one.key === "solutions_border_type_section"
            ).value
          } ${
            this.solutions.find(
              (one) => one.key === "solutions_border_color_section"
            ).value
          }`
        );

      document
        .querySelector(".solutions")
        .style.setProperty(
          "--solutions-border-bottom",
          `${
            this.solutions.find(
              (one) => one.key === "solutions_border_size_section"
            ).value
          }px ${
            this.solutions.find(
              (one) => one.key === "solutions_border_type_section"
            ).value
          } ${
            this.solutions.find(
              (one) => one.key === "solutions_border_color_section"
            ).value
          }`
        );
    } else if (
      this.solutions.find(
        (one) => one.key === "solutions_border_position_section"
      ) &&
      this.solutions.find(
        (one) => one.key === "solutions_border_position_section"
      ).value === "top"
    ) {
      document
        .querySelector(".solutions")
        .style.setProperty(
          "--solutions-border-top",
          `${
            this.solutions.find(
              (one) => one.key === "solutions_border_size_section"
            ).value
          }px ${
            this.solutions.find(
              (one) => one.key === "solutions_border_type_section"
            ).value
          } ${
            this.solutions.find(
              (one) => one.key === "solutions_border_color_section"
            ).value
          }`
        );
    } else if (
      this.solutions.find(
        (one) => one.key === "solutions_border_position_section"
      ) &&
      this.solutions.find(
        (one) => one.key === "solutions_border_position_section"
      ).value === "top"
    ) {
      document
        .querySelector(".solutions")
        .style.setProperty(
          "--solutions-border-bottom",
          `${
            this.solutions.find(
              (one) => one.key === "solutions_border_size_section"
            ).value
          }px ${
            this.solutions.find(
              (one) => one.key === "solutions_border_type_section"
            ).value
          } ${
            this.solutions.find(
              (one) => one.key === "solutions_border_color_section"
            ).value
          }`
        );
    }
  },
};
</script>
<style lang="scss">
.solutions {
  background-color: rgba(255, 255, 255, 0);
  background-image: url("https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/it_graph-1.jpg");
  background-position: center bottom;
  background-repeat: no-repeat;
  background-size: cover;
  padding-bottom: 130px;
  padding-left: 122px;
  padding-right: 122px;
  padding-top: 130px;

  --solutions-bg: #fff;
  --solutions-fontSize: 20px;
  --solutions-border-top: 0px solid #fff;
  --solutions-border-bottom: 0px solid #fff;

  background: var(--solutions-bg);
  border-top: var(--solutions-border-top);
  border-bottom: var(--solutions-border-bottom);
  background-repeat: no-repeat;
  background-size: cover;
  h2 {
    font-size: var(--solutions-fontSize);
  }
}
@include sm {
  .solutions {
    padding-left: 40px;
    padding-right: 40px;
  }
}
.solutions h2.heading {
  color: rgb(9, 41, 51);
  font-family: Teko;
  font-size: 65px;
  font-weight: 400;
  line-height: 65px;
  margin-bottom: 31px;
}
.solutions h2.heading span {
  color: rgb(116, 197, 218);
}
.solutions .seprator {
  width: 100px;
  margin-bottom: 50px;
  background-color: rgb(116, 197, 218);
  height: 4px;
}
.solutions p {
  color: rgb(118, 136, 148);
  font-family: Roboto;
  font-size: 16px;
  font-weight: 400;
  line-height: 30px;
  margin-bottom: 20px;
}
.solutions h2 {
  display: flex;
  align-items: center;
  gap: 10px;
}
.solutions .icon {
  animation: fusionExpandAndShow 1s 1 cubic-bezier(0.17, 0.67, 0.83, 0.67);
  width: 50px;
  height: 50px;
  border-radius: 50%;
  position: relative;
}
.solution .icon i {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: rgb(98, 57, 189);
  font-size: 20px;
  color: #fff;
  display: grid;
  place-items: center;
}
.solutions .solution h2 {
  color: rgb(9, 41, 51);
  cursor: pointer;
  font-family: Teko;
  font-size: 30px;
  font-weight: 400;
  line-height: 30px;
  margin-bottom: 15px;
}
.solutions .solution:hover h2 {
  color: rgb(98, 57, 189);
}
.solutions .solution:hover .icon::after {
  pointer-events: none;
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: inherit;
  content: "";
  box-sizing: content-box;
  top: 0;
  left: 0;
  padding: 0;
  z-index: 1;
  box-shadow: rgba(255, 255, 255, 0.1) 0px 0px 0px 2px,
    rgb(98, 57, 189) 0px 0px 10px 10px,
    rgba(255, 255, 255, 0.5) 0px 0px 0px 10px;
  opacity: 0;
  transform: scale(0.9);
  animation: fusionSonarEffect 1.3s ease-out 75ms infinite;
}
.solutions .solution .icon i {
  vertical-align: middle;
}
.solutions .solution p {
  color: rgb(118, 136, 148);
  cursor: pointer;
  font-family: Roboto;
  font-size: 16px;
  font-weight: 400;
  line-height: 30px;
  margin-bottom: 20px;
}
.solutions .btn {
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
}
.solutions .btn:hover {
  justify-content: center;
  color: rgb(255, 255, 255);
  background-color: var(--main-color);
  border: none;
}
.solutions .image img {
  transition: transform 0.35s linear;
}
.solutions .image img:hover {
  transform: perspective(1000px) scale(1.03);
}
@keyframes fusionSonarEffect {
  0% {
    opacity: 0.3;
  }
  40% {
    opacity: 0.5;
  }
  to {
    transform: scale(1.5);
    opacity: 0;
  }
}
</style>
