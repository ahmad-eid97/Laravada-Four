<template>
  <div class="bottom-banner">
    <div class="row m-0 justify-content-between align-items-center">
      <div class="col-lg-auto">
        <div class="title">
          <h2>
            {{
              bottomBanner.find((one) => one.key === "banner-bottom_title")
                .value
            }}
          </h2>
          <h4>
            {{
              bottomBanner.find(
                (one) => one.key === "banner-bottom_description"
              ).value
            }}<span>.</span>
          </h4>
        </div>
      </div>
      <div class="col-lg-auto mt-5">
        <div class="content">
          <a
            :href="
              bottomBanner.find((one) => one.key === 'banner-bottom_link').value
            "
            class="btn"
            >GET STARTED</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppHomeBottomBanner",
  props: ["bottomBanner"],
  data() {
    return {};
  },
  mounted() {
    document
      .querySelector(".bottom-banner")
      .style.setProperty(
        "--bannerBottom-bg",
        this.bottomBanner.find(
          (one) => one.key === "banner-bottom_background_active_section"
        ).value === "color"
          ? this.bottomBanner.find(
              (one) => one.key === "banner-bottom_background_color_section"
            ).value
          : `url(${
              this.bottomBanner.find(
                (one) => one.key === "banner-bottom_background_image_section"
              ).value
            })`
      );

    document
      .querySelector(".bottom-banner")
      .style.setProperty(
        "--bannerBottom-fontSize",
        `${
          this.bottomBanner.find(
            (one) => one.key === "banner-bottom_font_size_section"
          ).value
        }px`
      );

    if (
      this.bottomBanner.find(
        (one) => one.key === "banner-bottom_border_position_section"
      ) &&
      this.bottomBanner.find(
        (one) => one.key === "banner-bottom_border_position_section"
      ).value === "both"
    ) {
      document
        .querySelector(".bottom-banner")
        .style.setProperty(
          "--bannerBottom-border-top",
          `${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_size_section"
            ).value
          }px ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_type_section"
            ).value
          } ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_color_section"
            ).value
          }`
        );

      document
        .querySelector(".bottom-banner")
        .style.setProperty(
          "--bannerBottom-border-bottom",
          `${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_size_section"
            ).value
          }px ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_type_section"
            ).value
          } ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_color_section"
            ).value
          }`
        );
    } else if (
      this.bottomBanner.find(
        (one) => one.key === "banner-bottom_border_position_section"
      ) &&
      this.bottomBanner.find(
        (one) => one.key === "banner-bottom_border_position_section"
      ).value === "top"
    ) {
      document
        .querySelector(".bottom-banner")
        .style.setProperty(
          "--bannerBottom-border-top",
          `${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_size_section"
            ).value
          }px ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_type_section"
            ).value
          } ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_color_section"
            ).value
          }`
        );
    } else if (
      this.bottomBanner.find(
        (one) => one.key === "banner-bottom_border_position_section"
      ) &&
      this.bottomBanner.find(
        (one) => one.key === "banner-bottom_border_position_section"
      ).value === "top"
    ) {
      document
        .querySelector(".bottom-banner")
        .style.setProperty(
          "--bannerBottom-border-bottom",
          `${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_size_section"
            ).value
          }px ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_type_section"
            ).value
          } ${
            this.bottomBanner.find(
              (one) => one.key === "banner-bottom_border_color_section"
            ).value
          }`
        );
    }
  },
};
</script>
<style lang="scss">
.bottom-banner {
  background-color: rgb(98, 57, 189);
  background-position: center top;
  background-repeat: no-repeat;
  background-size: cover;
  /* background-image: url("https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/11/avada-it-call-to-action-bg.png"); */
  padding-bottom: 90px;
  padding-left: 30px;
  padding-right: 30px;
  padding-top: 90px;

  --bannerBottom-bg: #fff;
  --bannerBottom-fontSize: 20px;
  --bannerBottom-border-top: 0px solid #fff;
  --bannerBottom-border-bottom: 0px solid #fff;

  background: var(--bannerBottom-bg);
  border-top: var(--bannerBottom-border-top);
  border-bottom: var(--bannerBottom-border-bottom);
  background-repeat: no-repeat;
  background-size: cover;
  h2 {
    font-size: var(--bannerBottom-fontSize);
  }
}
.bottom-banner .title {
  margin: 15px 0;
  border-left: 12px solid #74c5da;
  padding: 0 30px;
}
.bottom-banner .title h2 {
  color: rgb(255, 255, 255);
  flex-grow: 0;
  font-family: Teko;
  font-size: 124px;
  font-style: normal;
  font-weight: 400;
  letter-spacing: normal;
  line-height: 124px;
}

.bottom-banner .title h4 {
  color: rgb(255, 255, 255);
  flex-grow: 0;
  font-family: Teko;
  font-size: 65px;
  font-style: normal;
  font-weight: 400;
  letter-spacing: normal;
  line-height: 65px;
}
.bottom-banner .title h4 span {
  color: rgb(116, 197, 218);
}

@include xs {
  .bottom-banner .title h2 {
    font-size: 70px;
    line-height: 80px;
  }

  .bottom-banner .title h4 {
    font-size: 45px;
    line-height: 60px;
  }
}

.bottom-banner .btn {
  border-radius: 25px 25px 25px 25px;
  padding-bottom: 17px;
  padding-left: 40px;
  padding-right: 40px;
  padding-top: 17px;
  font-weight: 500;
  justify-content: center;
  letter-spacing: 2px;
  font-size: 18px;
  background-color: rgb(255, 255, 255);
  color: #000;
  line-height: 17px;
  min-width: 200px;
  text-transform: uppercase;
  font-family: "Roboto";
  border: none;
}
.bottom-banner .btn:hover {
  justify-content: center;
  color: rgb(255, 255, 255);
  background-color: var(--main-color);
  border: none;
}
</style>
