<template>
    <div class="RoundMarkerBig">
        <div class="RoundMarkerBig__body">
            <div class="RoundMarkerBig__inner_body">
                <slot />
            </div>
        </div>

        <div :class="{ showBar: showBar }" class="RoundMarkerBig__bar" />
    </div>
</template>

<script>
export default {
    props: ['showBar'],
}
</script>

<style lang="scss" scoped>
.RoundMarkerBig {
    display: flex;
    flex-direction: row;
    align-items: center;

    &__body {
        width: 60px;
        height: 60px;

        cursor: pointer;

        background: $darkBlue;
        border-radius: 30px;

        display: flex;
        justify-content: center;
        align-items: center;
    }

    &__inner_body {
        width: 58px;
        height: 58px;

        border-radius: 29px;
        border: 4px white solid;

        display: flex;
        justify-content: center;
        align-items: center;

        font-size: 32px;
        color: white;
        font-weight: bold;
    }

    &__bar {
        border-top: 2px $darkBlue solid;
        width: 0;
    }

    .showBar {
        width: 21px;
    }
}
</style>
