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
    <div id="app">
        <div class="container">
            <CurrencyConverter />
        </div>
    </div>   
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";

#app {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-width: 100vw;
    height: 100vh;
    background-image: url(/public/img/Pattern.jpg);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center; 
}

.container {
    border: 5px solid #8CBA92;
    background-color: white;
    padding: 50px;
}
</style>
