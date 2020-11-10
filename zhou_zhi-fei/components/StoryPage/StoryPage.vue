<template>
    <div class="StoryPage" :class="{ fixMobileStoryNav: isStoryPageFull }">
        <MobileStoryNav v-if="showMobileStoryNav" :currentAge="currentAge" />

        <StoryNav class="StoryPage__nav" :currentChapter="currentChapter" />

        <div class="StoryPage__story_container">
            <Story1 />
            <Story2 />
        </div>
    </div>
</template>

<script>
import scrollama from 'scrollama'

import StoryNav from './StoryNav'
import MobileStoryNav from './MobileStoryNav'
import Story1 from './Story1'
import Story2 from './Story2'

// import 'intersection-observer'
export default {
    components: {
        MobileStoryNav,
        StoryNav,
        Story1,
        Story2,
    },

    data() {
        return {
            isStoryPageFull: false,
            showMobileStoryNav: false,
            currentChapter: '1',
            currentAge: '02',
        }
    },

    mounted() {
        // ---------------Handle storyNav fix-----------------
        const scrollerStoryNav = scrollama()
        scrollerStoryNav
            .setup({
                step: '.StoryPage',
                offset: 0,
            })
            .onStepEnter((response) => {
                this.isStoryPageFull = true
                this.showMobileStoryNav = true
            })
            .onStepExit((response) => {
                this.isStoryPageFull = false
                this.showMobileStoryNav = false
            })

        window.addEventListener('resize', scrollerStoryNav.resize)
        // ---------------Handle roundMarker animation-----------------
        const scrollerStorys = scrollama()
        const scrollerRoundMarkerAge = scrollama()

        scrollerStorys
            .setup({
                step: '.age_section',
                offset: 0.2,
            })
            .onStepEnter((response) => {
                const { element } = response
                element.children[0].classList.add('RoundMarkerBig_fix')

                this.currentChapter = element.parentElement.id
            })
            .onStepExit((response) => {
                const { element } = response
                element.children[0].classList.remove('RoundMarkerBig_fix')
            })

        scrollerRoundMarkerAge
            .setup({
                step: '.age_section',
                offset: 0.6,
            })
            .onStepEnter((response) => {
                const { element } = response

                this.currentAge = element.children[0].id
            })

        window.addEventListener('resize', scrollerRoundMarkerAge.resize)
    },
}
</script>

<style lang="scss">
.StoryPage {
    z-index: 10;
    min-height: 100vh;
    background: white;
    padding: 0 20px 40px;

    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;

    &__nav {
        display: none !important;
    }

    &__story_container {
        width: 100%;
        padding: 100px 0 40px;
    }

    .MobileStoryNav {
        display: block;
    }

    @include atMedium {
        padding: 0 0 40px;

        flex-direction: row;
        align-items: flex-start;
        justify-content: flex-end;

        .MobileStoryNav {
            display: none;
        }

        &__nav {
            display: flex !important;

            width: 30%;
        }

        &__story_container {
            padding-left: 70px;
            width: 70%;
        }
    }

    @include atLarge {
        padding: 0 0 40px;

        flex-direction: row;
        align-items: flex-start;
        justify-content: flex-end;

        .MobileStoryNav {
            display: none;
        }

        &__nav {
            display: flex;

            width: 36%;
        }

        &__story_container {
            padding-left: 128px;
            width: 64%;
        }
    }
}

.fixMobileStoryNav {
    @include atMedium {
        .StoryPage__nav {
            position: fixed;
            top: 0%;
            left: 0;

            width: 30%;
        }
    }

    @include atLarge {
        .StoryPage__nav {
            position: fixed;
            top: 0%;
            left: 0;

            width: 36%;
        }
    }
}

.age_section {
    position: relative;
    padding-bottom: 1px;

    .RoundMarkerBig {
        position: absolute;
        left: -100px;
        top: 0;

        @include atLarge {
            left: -158px;
        }
    }

    .RoundMarkerBig_fix {
        position: fixed;
        top: 20%;

        left: calc(30% - 30px);

        @include atLarge {
            left: calc(36% - 30px);
        }
    }
}
</style>
