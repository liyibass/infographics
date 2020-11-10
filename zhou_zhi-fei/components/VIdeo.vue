<template>
    <div class="Video">
        <!-- <client-only>
            <youtube
                video-id="Dx5qFachd3A"
                host="https://www.youtube-nocookie.com"
            ></youtube>
        </client-only> -->
        <iframe
            width="640"
            height="360"
            :src="`https://www.youtube.com/embed/${videoId}?autoplay=0&loop=0&controls=1&rel=1`"
            frameborder="0"
            allowfullscreen
        ></iframe>
    </div>
</template>

<script>
export default {
    data() {
        return {
            videoId: 'Dx5qFachd3A',
        }
    },
}
</script>

<style lang="scss" scoped>
.Video {
    z-index: 20;
    position: relative;
    height: 100vh;
    background: $darkBlue;

    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
