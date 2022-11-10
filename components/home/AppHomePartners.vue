<template>
    <section class="partners">
                
        <swiper
            :options="swiperOption"
            class="owl-carousel"
        >

            <swiper-slide>
                <div class="item">
                <img class="imgo" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-2-1-320x202.jpg" width="150" height="150">
                </div>
            </swiper-slide>

            <swiper-slide>
                <div class="item">
                <img class="imgo" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-320x202.png" width="150" height="150">
                </div>
            </swiper-slide>

            <swiper-slide>
                <div class="item">
                <img class="imgo" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-3-1-320x202.jpg" width="150" height="150">
                </div>
            </swiper-slide>

            <swiper-slide>
                <div class="item">
                <img class="imgo" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-2-1-320x202.jpg" width="150" height="150">
                </div>
            </swiper-slide>

            <swiper-slide>
                <div class="item">
                <img class="imgo" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/cloud-logo-320x202.png" width="150" height="150">
                </div>
            </swiper-slide>

            <swiper-slide>
                <div class="item">
                    <img class="imgo" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-1-1-320x202.jpg" width="150" height="150">
                </div>
            </swiper-slide>

        </swiper>
    </section>
</template>

<script>

export default {
    name: 'AppHomePartners',
    data() {
        return {
            swiperOption: {
            loop: true,
            slidesPerView: 5,
            spaceBetween: 50,
            breakpoints: {
                // when window width is >= 320px
                100: {
                slidesPerView: 1,
                spaceBetween: 5,
                },
                // when window width is >= 480px
                480: {
                slidesPerView: 2,
                spaceBetween: 5,
                },
                // when window width is >= 640px
                640: {
                slidesPerView: 3,
                spaceBetween: 5,
                },
                992: {
                slidesPerView: 4,
                spaceBetween: 5,
                },
                1200: {
                slidesPerView: 5,
                spaceBetween: 5,
                },
            }
            },
        }
    }
}
</script>
<style>
    .partners {
        padding: 10px 100px 40px;
    }
    .partners .owl-carousel {
        margin-bottom: 40px;
    }
    .partners .owl-carousel .item  {
        text-align: center;
    }
    .partners .owl-carousel .item img {
        max-height: 115px;
        width: auto;
        display: inline;
        max-width: 100%;
        height: auto;
    }


</style>