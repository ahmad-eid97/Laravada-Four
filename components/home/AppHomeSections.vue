<template>
    <div class="sections">
       <div class="row m-0">
            <div class="col-lg section">
                <div class="heading text-center">
                    <a href="#">
                        <img class="img-fluid" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-3-1.jpg" alt="">
                    </a>
                </div>
                <p>
                    “Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Mauris consequat, mauris sed tincidunt maximus, quam felis vulputate augue, et finibus lorem est vel odios.”
                </p>
            </div>
            <div class="col-lg section bordered">
                <div class="heading text-center">
                    <a href="#">
                        <img class="img-fluid" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object-2-1.jpg" alt="">
                    </a>
                </div>
                <p>
                    “Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Mauris consequat, mauris sed tincidunt maximus, quam felis vulputate augue, et finibus lorem est vel odios.”
                </p>
            </div>
            <div class="col-lg section">
                <div class="heading text-center">
                    <a href="#">
                        <img class="img-fluid" src="https://avada.theme-fusion.com/information-technology/wp-content/uploads/sites/81/2016/10/Vector-Smart-Object.png" alt="">
                    </a>
                </div>
                <p>
                    “Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Mauris consequat, mauris sed tincidunt maximus, quam felis vulputate augue, et finibus lorem est vel odios.”
                </p>
            </div>
           
       </div>
    </div>
</template>

<script>
export default {
    name: 'AppHomeSections',
    data() {
        return {

        }
    }
}
</script>
<style lang="scss">
    .section {
        padding-bottom: 45px;
        padding-left: 30px;
        padding-right: 30px;
        padding-top: 45px
    }

    .section p {
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
    @include xs {
        .heading img {
            width: 220px;
        }

        .section p {
            font-size: 18px;
            line-height: 28px;
        }
    }
</style>