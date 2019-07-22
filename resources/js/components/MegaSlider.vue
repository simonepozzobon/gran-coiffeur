<template>
<div class="gc-mega-slider">
    <swiper
        ref="mySwiper"
        :options="swiperOption"
        @someSwiperEvent="callback"
    >
        <!-- slides -->
        <swiper-slide>
            <mega-slide src="/images/slide_1.JPG">
                <template slot="head">10 giorni - 10€ di sconto</template>
                Sui trattamenti corpo e capelli
                <template slot="button">Approfittane Ora</template>
            </mega-slide>
        </swiper-slide>
        <swiper-slide>
            <mega-slide src="/images/slide_2.JPG">
                <template slot="head">Young Summer Styling</template>
                scopri i nuovi prodotti di hair styling, perfetti per strutturare il tuo look
                <template slot="button">Scopri di più</template>
            </mega-slide>
        </swiper-slide>
        <swiper-slide>
            <mega-slide src="/images/slide_3.JPG">
                <template slot="head">New Botanical Lab</template>
                scopri i nuovi proditti a base di cheratina, per fortificare i tuoi capelli al mare
                <template slot="button">Scopri di più</template>
            </mega-slide>
        </swiper-slide>
        <!-- Optional controls -->
        <div
            class="swiper-pagination"
            slot="pagination"
        ></div>
        <div
            class="swiper-button-prev"
            slot="button-prev"
        ></div>
        <div
            class="swiper-button-next"
            slot="button-next"
        ></div>
        <div
            class="swiper-scrollbar"
            slot="scrollbar"
        ></div>
    </swiper>
</div>
</template>

<script>
import MegaSlide from './MegaSlide.vue'
import {
    swiper,
    swiperSlide
}
from 'vue-awesome-swiper'

import 'swiper/dist/css/swiper.css'

export default {
    name: 'MegaSlider',
    components: {
        MegaSlide,
        swiper,
        swiperSlide,
    },
    data: function () {
        return {
            swiperOption: {
                // some swiper options/callbacks
                // 所有的参数同 swiper 官方 api 参数
                // ...
            }
        }
    },
    methods: {
        callback: function () {

        }
    },
}
</script>

<style lang="scss" scoped>
@import '~styles/shared';

.swiper-button-next {
    width: $spacer;
    height: $spacer;
    right: 2.2%;
    left: auto;
    filter: brightness(0%) invert(1);
    background-size: contain;
}
.swiper-button-prev {
    width: $spacer;
    height: $spacer;
    left: 2.2%;
    right: auto;
    filter: brightness(0%) invert(1);
    background-size: contain;
}
</style>
