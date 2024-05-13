<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import CurrencyConverter from './components/CurrencyConverter.vue';

export default {
    data() {
        return {

        };
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter,
        CurrencyConverter
    },  
    methods: {

    }
}
</script>

<template>
    <h1>
        Mia App
    </h1>

    <AppHeader />

    <AppMain />

    <AppFooter />

    <CurrencyConverter />
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";
</style>
