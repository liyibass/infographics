<template>
    <div class="Credit">
        <div class="Credit__container">
            <span>
                記者：陳虹瑾<br />
                攝影： <br />
                網頁製作：呂理詣、陳怡蒨、李又如、陳玟諺、陳姿廷、簡信昌
            </span>
            <span class="Credit__container_date">2020-11-06</span>
        </div>
    </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.Credit {
    z-index: 20;
    position: relative;
    background: $darkBlue;
    padding: 30px 30px;

    font-size: 14px;
    font-weight: 500;
    line-height: 1.71;
    text-align: center;
    color: #ffffff;

    &__container {
        display: flex;
        flex-direction: column;
        align-items: center;

        &_date {
            font-weight: normal;
        }
    }
}
</style>
