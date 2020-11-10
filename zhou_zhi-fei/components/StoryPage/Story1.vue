<template>
    <div class="Story" id="1">
        <div class="age_section">
            <RoundMarkerBig id="02">02</RoundMarkerBig>

            <ArticleTitle
                >Ch1<br />
                2-8 歲 肥肉、白蛆、遛狗鏈</ArticleTitle
            >

            <ArticleParagraph>
                <p>
                    許多年以後，周子飛在餐廳打工，瞥見廚房餿水桶裡翻動著的白白的蛆，忽然想起童年的菜色。他頓悟了：原來，人類世界裡，是沒人拿蛆作為食物的。又過了許多年，四十三歲的周子飛坐在我們面前，腦中閃過這些畫面，他忽然有點納悶：「一般小孩吃蛆，是不是會有什麼病？是不是會死掉？」他又問，「後來我想想，ㄟ，我有吃蛆。那為什麼我到現在，還是一個健康（的人）？」
                </p>
            </ArticleParagraph>

            <ArticlePicture :imageUrl="imageCarousel" :autoplayTimeout="5000"
                >照片圖說照片圖說照片圖說照片圖說照片圖說照片圖說</ArticlePicture
            >
        </div>

        <div class="age_section">
            <RoundMarkerBig id="08">08</RoundMarkerBig>

            <ArticleSubTitle>被偷走的那六年</ArticleSubTitle>

            <ArticleParagraph>
                <p>
                    一九八零年初，育有十一名子女、住在新竹縣五峰鄉的泰雅族原住民周瑞霖以新台幣五萬元的「售價」，將九歲的三子周文星賣給山下的榮民張雄作為養子，周文星從此改名張文星。數月後，張文星自行翻開屋頂瓦片，逃離「新爸爸」家；張雄不甘，再上山，趁周瑞霖夫婦農忙，抱走年僅兩歲的周子飛「抵債」。也許是怕周子飛逃跑，張雄將兩歲兒關起來，這場囚錮，長達六年之久。
                </p>

                <p>
                    整整六年，周子飛與原生家庭斷了聯繫。六年裡，周瑞霖曾試圖找張雄要回兒子卻遭拒。後來他對外表示，自己身體不好，識字不多，長達六年要不回孩子，卻不懂得報警。
                </p>

                <p>
                    一九八六年三月，周瑞霖、十五歲的張文星終於帶著警方前來張雄家，救出周子飛。一同被救出的，還有張雄買來、囚禁多年的妻子郭關關。眾人這才發現，郭關關、張雄與周子飛，三人皆無法言語－－郭關關是瘖啞人士且患有精神疾病，張雄則疑因戰爭或疾病傷了聲帶，導致又聾又啞；本該是學齡兒童的周子飛時年八歲，不聾不啞且聲帶正常，卻嗚咽咿啞，長年被囚且無人對話，完全無法使用語言。
                </p>

                <p>
                    時值台灣解嚴前後，此事一度在新聞上沸揚。此後兩年間，媒體多稱周子飛為「啞童」，與之伴隨的詞彙大約不脫「猴兒似地」、「猴童」、「狼童」云云，亦有報章形容這是「折翅乳燕」的離奇境遇。沉寂多年後，二零零二年，二十五歲的周子飛被發現在投注站賣公益彩券，彼時網路媒體甫興，記者湧入投注站，用詞不脫二十年前範疇，故事以極具張力的方式擴散：「半人半獸」的「猴童」長大成人，入世賣彩券了。
                </p>
            </ArticleParagraph>

            <ArticleBlank />
        </div>

        <!-- <ArticlePicture></ArticlePicture> -->
    </div>
</template>

<script>
import ArticleTitle from '~/components/ArticleComponents/ArticleTitle'
import ArticleParagraph from '~/components/ArticleComponents/ArticleParagraph'
import ArticleSubTitle from '~/components/ArticleComponents/ArticleSubTitle'
import ArticlePicture from '~/components/ArticleComponents/ArticlePicture'
import ArticleBlank from '~/components/ArticleComponents/ArticleBlank'
import RoundMarkerBig from '~/components/RoundMarkerBig'

import image1 from '~/static/images/story1_3_1.jpeg'
import image2 from '~/static/images/story1_3_2.jpeg'
import image3 from '~/static/images/story1_3_3.jpeg'
export default {
    components: {
        ArticleTitle,
        ArticleParagraph,
        ArticleSubTitle,
        ArticlePicture,
        ArticleBlank,
        RoundMarkerBig,
    },
    data() {
        return {
            imageCarousel: [image1, image2, image3],
        }
    },
}
</script>

<style lang="scss" scoped>
.Story {
    position: relative;
    @include atMedium {
        width: 400px;
    }
}
</style>
