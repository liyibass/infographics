<template>
    <div class="PictureContainer">
        <div
            class="PictureContainer__img"
            :class="{ zoom: zoom }"
            @click="zoomImg"
            @mouseover="stopAutoplay"
            @mouseout="startAutoplay"
        >
            <div class="PictureContainer__img_container">
                <transition :name="animationState">
                    <img :key="current" :src="imageUrl[current]" />
                </transition>
            </div>
        </div>

        <div class="PictureContainer__content">
            <slot />
        </div>

        <div v-if="imageUrl.length > 1" class="PictureContainer__navigation">
            <div class="PictureContainer__navigation_arrow">
                <div class="arrow_prev" @click="prevImg">
                    <img :src="prevArrow" alt="arrow" />
                </div>
                <div class="arrow_next" @click="nextImg">
                    <img :src="nextArrow" alt="arrow" />
                </div>
            </div>

            <div
                v-for="(selection, index) in imageUrl"
                :key="index"
                class="PictureContainer__navigation_selection"
                :class="{ selected: current === index }"
                @click="selectionHandler(index)"
                @mouseover="stopAutoplay"
                @mouseout="startAutoplay"
            ></div>
        </div>
    </div>
</template>

<script>
import prevArrow from '~/static/images/logo/arrow-left.png'
import nextArrow from '~/static/images/logo/arrow-right.png'
import gaMixin from '~/mixins/gaMixin'

export default {
    props: ['imageUrl', 'autoplayTimeout'],
    mixins: [gaMixin],
    data() {
        return {
            current: 0,
            next: 1,
            animationState: 'slide-next',

            autoplayInterval: {},
            zoom: false,
            prevArrow,
            nextArrow,
        }
    },
    methods: {
        selectionHandler(index) {
            if (index > this.current) {
                this.animationState = 'slide-next'
            } else {
                this.animationState = 'slide-prev'
            }
            this.current = index
        },
        nextImg() {
            const next =
                this.current + 1 > this.imageUrl.length - 1
                    ? 0
                    : this.current + 1
            this.selectionHandler(next)
        },
        prevImg() {
            const next =
                this.current - 1 < 0
                    ? this.imageUrl.length - 1
                    : this.current - 1
            this.selectionHandler(next)
        },
        startAutoplay() {
            this.autoplayInterval = setInterval(() => {
                this.nextImg()
            }, this.autoplayTimeout)
        },
        stopAutoplay() {
            clearInterval(this.autoplayInterval)
        },
        zoomImg(e) {
            this.zoom = !this.zoom

            if (!this.zoom) return
            this.gaClickHandler('文內圖片')
        },
    },
}
</script>

<style lang="scss" scoped>
.PictureContainer {
    width: 100%;
    margin: auto;
    margin-bottom: 40px;
    &__img {
        cursor: pointer;
        position: relative;
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;

        margin-bottom: 10px;
        &_container {
            // width: 100%;
            overflow: hidden;
            display: flex;
            flex-direction: row;
            img {
                width: 100%;
                height: 100%;
            }
        }
    }

    @include atSmall {
        width: 100%;
        &__img {
            &_container {
                width: 100%;
            }
        }
    }

    @include atMedium {
        width: 360px;
        &__img {
            &_container {
                width: 800px;
            }
        }
    }

    &__content {
        width: 100%;
        font-size: 15px;
        font-weight: normal;

        color: #4a4a4a;
    }

    a {
        color: #006db2;
    }

    &__navigation {
        position: relative;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        margin-top: 20px;
        height: 34px;

        &_selection {
            z-index: 2;
            width: 14px;
            height: 14px;
            border: solid 1px $lightBlue;
            background-color: #ffffff;
            border-radius: 7px;

            margin-right: 20px;
            &:last-child {
                margin-right: 0;
            }
            cursor: pointer;
        }

        &_arrow {
            z-index: 1;
            // background: gold;
            position: absolute;
            width: 100%;
            height: 100%;

            display: flex;
            flex-direction: row;
            justify-content: space-between;

            color: $lightBlue;
            .arrow_prev,
            .arrow_next,
            img {
                cursor: pointer;
                height: 34px;
            }
        }
    }

    .selected {
        background-color: $lightBlue;
    }

    .zoom {
        width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;
        background: rgba(0, 0, 0, 0.8);
        z-index: 999;

        img {
            max-width: 800px;
        }
    }
}

.slide-next-enter-active,
.slide-next-leave-active,
.slide-prev-enter-active,
.slide-prev-leave-active {
    transition: all 0.5s;
}

.slide-next-enter,
.slide-next-leave {
    transform: translateX(0);
}
.slide-next-enter-to,
.slide-next-leave-to {
    transform: translateX(-100%);
}

.slide-prev-enter {
    transform: translateX(-200%);
}
.slide-prev-enter-to {
    transform: translateX(-100%);
}
.slide-prev-leave {
    transform: translateX(0);
}
.slide-prev-leave-to {
    transform: translateX(100%);
}
</style>
