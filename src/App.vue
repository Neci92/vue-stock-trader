<template>
<div>
    <div class="container">
    <app-header></app-header>
    <div class="row">
        <div class="col-xs-12">
            <transition name="slide" mode="out-in">
                <router-view></router-view>
            </transition>
        </div>
    </div>
    </div>
</div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.min.css'
import Header from './components/Header'

    export default {
        components: {
            appHeader: Header
        },
        created() {
            this.$store.dispatch('initStocks');
        }
    }
</script>

<style lang="scss" scoped>
    body {
        padding: 30px;
    }

    .slide {
        &-enter-active {
            animation: slide-in .2s ease-out forwards
        }

        &-leave-active {
            animation: slide-out .2s ease-out forwards
        }
    }

    @keyframes slide-in {
        from {
            transform: translateY(-30px);
            opacity: 0;
        }
         
        to {
            transform: translateY(0);
            opacity: 1;
        }
    }

    @keyframes slide-out {
        from {
            transform: translateY(0);
            opacity: 1;
        }
         
        to {
            transform: translateY(30px);
            opacity: 0;
        }
    }
</style>

