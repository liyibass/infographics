<template>
    <div class="StoryPage" :class="{ fixMobileStoryNav: isStoryPageFull }">
        <MobileStoryNav />

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
            currentChapter: 1,
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
            })
            .onStepExit((response) => {
                this.isStoryPageFull = false
            })

        window.addEventListener('resize', scrollerStoryNav.resize)
        // ---------------Handle roundMarker animation-----------------
        const scrollerRoundMarkers = scrollama()
        const scrollerStorys = scrollama()

        // scrollerRoundMarkers
        //     .setup({
        //         step: '.RoundMarkerBig',
        //         offset: 0.2,
        //     })
        //     .onStepEnter((response) => {
        //         const { element } = response
        //         element.classList.add('RoundMarkerBig_fix')
        //     })
        //     .onStepExit((response) => {
        //         const { direction, element } = response
        //         if (direction === 'down') return

        //         element.classList.remove('RoundMarkerBig_fix')
        //     })

        scrollerStorys
            .setup({
                step: '.Story',
                offset: 0.15,
            })
            .onStepEnter((response) => {
                const { element } = response
                element.children[0].classList.add('RoundMarkerBig_fix')

                this.currentChapter = element.id
            })
            .onStepExit((response) => {
                const { element } = response
                element.children[0].classList.remove('RoundMarkerBig_fix')
            })
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
        display: none;
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
            display: flex;

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
    top: 15%;

    left: calc(30% - 30px);

    @include atLarge {
        left: calc(36% - 30px);
    }
}
</style>
