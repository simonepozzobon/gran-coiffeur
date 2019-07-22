<template>
<div class="main-container">
    <nav-bar />
    <router-view />
</div>
</template>

<script>
import NavBar from './NavBar.vue'
export default {
    name: 'MainTemplate',
    components: {
        NavBar
    }
}
</script>

<style lang="scss" scoped>
@import '~styles/shared';

.main-container {
    width: 100%;
    min-height: 100vh;
}
</style>
