<template>
    <div class="ArticleSubTitle">
        <slot />
    </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.ArticleSubTitle {
    font-size: 21px;
    color: #4a4a4a;

    margin-bottom: 30px;

    @include atSmall {
    }
}
</style>
