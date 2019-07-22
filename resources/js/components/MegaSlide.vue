<template>
<div class="mega-slide">
    <div class="mega-slide__container">
        <div
            ref="container"
            class="mega-slide__image"
        ></div>
        <img
            :src="src"
            alt=""
            class="mega-slide__image-clean"
        >
        <div class="mega-slide__overlay-x"></div>
        <div class="mega-slide__overlay-y"></div>
        <div class="mega-slide__overlay-d"></div>
        <div class="mega-slide__content">
            <h1 class="mega-slide__head">
                <slot name="head"></slot>
            </h1>
            <p class="mega-slide__text">
                <slot></slot>
            </p>
            <a
                class="mega-slide__button btn btn-outline-gc-green"
                href="#"
            >
                <slot name="button"></slot>
            </a>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'MegaSlide',
    props: {
        src: {
            type: String,
            default: null,
        },
    },
    mounted: function () {
        let el = this.$refs.container
        // let elClean = this.$refs.containerClean
        el.style.backgroundImage = 'url(' + this.src + ')'
        // elClean.style.backgroundImage = 'url(' + this.src + ')'
        // elClean.style.backgroundImage = 'url(' + this.src + ')';
    }
}
</script>

<style lang="scss" scoped>
@import '~styles/shared';
.mega-slide {
    position: relative;
    overflow: hidden;
    padding: $spacer * 3;
    margin: $spacer * 1.25;
    // background-color: $gc-black;

    &__image {
        position: absolute;
        width: 100%;
        left: 0;
        top: 0;
        height: 100%;
        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
        filter: blur($spacer / 2 / 1.618) grayscale(100%);
        // z-index: 1;
        // display: none;
    }

    &__image-clean {
        position: absolute;
        width: 100%;
        height: auto;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        mask-image: linear-gradient(-125deg, rgba(#1E1A1E, 1) 0%, rgba(#1E1A1E,0) 58%); // background-image: linear, left top, left bottom, from(rgba(50,50,50,0.8)), to(rgba(80,80,80,0.2)), color-stop(.5,#333333);
        z-index: 1;
    }

    &__overlay-x {
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
        @include gradient-x-three-colors(rgba($gc-black, 0.9), rgba($gc-black, 0.4), 65%, rgba($gc-black, 0));
        z-index: 2;
    }

    &__overlay-y {
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
        @include gradient-y-three-colors(rgba($gc-black, 0), rgba($gc-black, 0.4), 75%, rgba($gc-black, 0.9));
        z-index: 2;
    }

    &__overlay-d {
        position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
        @include gradient-directional(rgba($gc-black, .56), rgba($gc-black, 0), 30deg);
        z-index: 2;
    }

    &__container {
        margin: ($spacer * 5) auto;
    }

    &__content {
        position: relative;
        z-index: 3;
    }

    &__head {
        color: $white;
        font-size: $display4-size;
        text-transform: uppercase;
        font-weight: bold;
    }

    &__text {
        color: $white;
        font-weight: $font-weight-light;
    }

    &__button {
        z-index: 3;
    }
}
</style>
