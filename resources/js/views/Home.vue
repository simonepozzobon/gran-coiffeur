<template>
<div>
    <mega-slider></mega-slider>
    <div class="d-md-flex flex-md-equal w-100">
        <block theme="gc-black">
            <template slot="head">
                Servizi
            </template>
        </block>
        <block
            type="image"
            src="/images/home_1.JPG"
        />
    </div>
    <div class="d-md-flex flex-md-equal w-100">
        <block
            theme="light"
            type="image"
            src="/images/home_2.jpg"
        />
        <block theme="gc-black">
            <template slot="head">
                Chi Siamo
            </template>
        </block>
    </div>
    <div class="d-md-flex flex-md-equal w-100">
        <block theme="gc-black">
            <template slot="head">
                Chi Siamo
            </template>
        </block>
        <block
            theme="light"
            type="image"
            src="/images/home_3.JPG"
        />
    </div>
</div>
</template>

<script>
import Block from '../components/Block.vue'
import MegaSlider from '../components/MegaSlider.vue'

export default {
    name: 'Home',
    components: {
        Block,
        MegaSlider
    }
}
</script>

<style lang="scss" scoped>
@import '~styles/shared';
</style>
