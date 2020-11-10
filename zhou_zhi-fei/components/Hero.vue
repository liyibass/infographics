<template>
    <div class="Hero">
        <div class="Hero__background">
            <div class="Hero__background_mask" />
            <img :src="bgMobile" alt="" />
        </div>

        <div class="Hero__wrapper">
            <div class="Hero__title">
                <div class="Hero__title_title">
                    <img :src="title" alt="" />
                </div>
                <div class="Hero__title_name">周子飛</div>
                <div class="Hero__title_info">
                    <div class="Hero__title_info_color" />
                    國工全我會了幾長興的，得己重工法：有中的士條，微高表下內親驚度舉樣人同力立我？散態拿不爭人帶生到醫和年來：客喜行再境動主！提科多有著的持領。
                </div>

                <div class="Hero__title_color_top_left"></div>
                <div class="Hero__title_color_bottom_right"></div>
            </div>

            <div class="Hero__mobile_info">
                國工全我會了幾長興的，得己重工法：有中的士條，微高表下內親驚度舉樣人同力立我？散態拿不爭人帶生到醫和年來：客喜行再境動主！提科多有著的持領。
            </div>
        </div>
    </div>
</template>

<script>
import bgMobile from '../static/images/bg_mobile.jpg'
import title from '../static/images/title.png'
export default {
    data() {
        return {
            bgMobile,
            title,
        }
    },
}
</script>

<style lang="scss" scoped>
.Hero {
    z-index: 20;
    position: relative;
    height: 100vh;
    background: $lightBlue;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background: black;

    &__background {
        z-index: 21;
        position: absolute;
        overflow: hidden;
        &_mask {
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.3);
        }
        img {
            width: 100%;
        }
    }

    &__wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    &__mobile_info {
        z-index: 22;
        background: black;
        padding: 41px 40px 22px;

        font-size: 1rem;
        font-weight: 500;
        line-height: 1.75;
        text-align: justify;
        color: #ffffff;

        @include atSmall {
            display: none;
        }
    }

    &__title {
        z-index: 22;
        position: relative;
        flex-grow: 1;

        &_title {
            z-index: 23;
            width: 160px;
            position: absolute;

            left: 10px;
            bottom: 42px;

            img {
                width: 100%;
            }
        }

        &_name {
            z-index: 23;
            position: absolute;
            right: 20px;
            bottom: 14px;

            font-size: 40px;
            font-weight: 300;
            color: #ffffff;
        }

        &_info {
            z-index: 23;
            width: 240px;
            position: absolute;

            display: none;
            font-size: 16px;
            font-weight: 500;
            line-height: 1.75;
            text-align: justify;
            color: #ffffff;

            &_color {
                width: 60px;
                height: 30px;
                background-color: #f5ecf1;
                margin-bottom: 10px;
            }
        }

        &_color {
            &_top_left {
                background: $lightBlue;
                width: 27px;
                height: 120px;

                position: absolute;
                left: 0;
            }
            &_bottom_right {
                background: $lightBlue;
                width: 200px;
                height: 15px;

                position: absolute;
                bottom: 23px;
                right: 0;
            }
        }
    }

    @include atSmall {
        &__background {
            display: none;
        }

        &__title {
            z-index: 22;
            position: relative;
            flex-grow: 1;

            &_title {
                width: 200px;
                position: absolute;

                left: 46px;
                bottom: 86px;

                img {
                    width: 100%;
                }
            }

            &_name {
                z-index: 23;
                position: absolute;
                left: 235px;
                bottom: 28px;

                font-size: 60px;

                color: #ffffff;
            }

            &_info {
                display: block;
                right: 52px;
                bottom: 194px;
            }

            &_color {
                &_top_left {
                    width: 30px;
                    height: 190px;
                    right: auto;
                    left: 0;
                }
                &_bottom_right {
                    width: 300px;
                    height: 15px;

                    bottom: 54px;
                    left: 177px;
                }
            }
        }
    }

    @include atMedium {
        &__title {
            z-index: 22;
            position: relative;
            flex-grow: 1;

            &_title {
                width: 250px;
                position: absolute;

                left: 46px;
                bottom: 36px;

                img {
                    width: 100%;
                }
            }

            &_name {
                z-index: 23;
                position: absolute;
                left: 335px;
                bottom: 28px;

                font-size: 70px;

                color: #ffffff;
            }

            &_info {
                right: 82px;
                bottom: 124px;
            }

            &_color {
                &_top_left {
                    width: 37px;
                    height: 190px;
                    right: 60px;
                    left: auto;
                }
                &_bottom_right {
                    width: 290px;
                    height: 17px;

                    bottom: 54px;
                    left: 307px;
                }
            }
        }
    }

    @include atLarge {
        &__title {
            z-index: 22;
            position: relative;
            flex-grow: 1;

            &_title {
                width: 311px;
                position: absolute;

                left: 46px;
                bottom: 36px;

                img {
                    width: 100%;
                }
            }

            &_name {
                z-index: 23;
                position: absolute;
                left: 415px;
                bottom: 28px;

                font-size: 80px;

                color: #ffffff;
            }

            &_info {
                right: 82px;
                bottom: 64px;
            }

            &_color {
                &_top_left {
                    width: 37px;
                    height: 190px;
                    right: 60px;
                    left: auto;
                }
                &_bottom_right {
                    width: 400px;
                    height: 20px;

                    bottom: 64px;
                    left: 357px;
                }
            }
        }
    }
}
</style>
