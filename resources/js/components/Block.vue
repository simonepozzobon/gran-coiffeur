<template>
<div
    class="gc-block"
    :class="[colorClass, typeClass]"
>
    <div
        ref="container"
        class="gc-block__container"
        :class="themeClass"
    >
        <div
            class="gc-block__text"
            v-if="type != 'image'"
        >
            <h2 class="display-5">
                <slot name="head"></slot>
            </h2>
            <p class="lead">And an even wittier subheading.</p>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'Block',
    props: {
        theme: {
            type: String,
            default: 'black',
        },
        type: {
            type: String,
            default: null,
        },
        src: {
            type: String,
            default: null,
        },
    },
    computed: {
        themeClass: function () {
            if (this.theme) {
                return 'bg-' + this.theme
            }
        },
        colorClass: function () {
            if (this.theme == 'light') {
                return 'gc-block--light'
            }
        },
        typeClass: function () {
            if (this.type === 'image') {
                return 'gc-block--image'
            }
        }
    },
    methods: {
        setSize: function () {
            let el = this.$refs.container
            let width = Math.floor(el.getBoundingClientRect().width)
            let height = width * 9 / 16
            el.style.minHeight = height + 'px'
            console.log(width);
        },
        setBg: function () {
            let el = this.$refs.container
            el.style.backgroundImage = 'url(' + this.src + ')'
        }
    },
    mounted: function () {
        if (this.type === 'image' && this.src) {
            this.setSize()
            this.setBg()
        }
    },
}
</script>

<style lang="scss" scoped>
@import '~styles/shared';

.gc-block {
    width: 100%;

    &__container {
        width: 100%;
        height: 100%;
        padding: $spacer * 3;
        text-align: center;
        color: $white;
        overflow: hidden;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    &__text {
        margin-top: $spacer * 3;
        margin-bottom: $spacer * 3;
        padding-top: $spacer * 3;
        padding-bottom: $spacer * 3;
    }

    &--light &__container {
        color: $black;
    }

    &--image &__container {
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
    }
}
</style>
