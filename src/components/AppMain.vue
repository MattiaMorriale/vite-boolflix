<script>

    import {store} from '../store.js';

    import AppCard from '../components/AppCard.vue'

    export default {

        name: 'AppMain',

        data() {
            return {

                store,

            }
        },

        components: {

            AppCard,

        }
        
    }

</script>

<template>

    <div class="py-4 w-100 d-flex justify-content-center" v-if="store.movie.length != 0">
        <h2>Film</h2>
    </div>
    <div class="box px-5 py-3 d-flex flex-wrap">
        
        <AppCard v-for="currentMovie in store.movie" :item="currentMovie"></AppCard>
    </div>
    <div class="py-4 w-100 d-flex justify-content-center" v-if="store.series.length!= 0">
        <h2>Serie Tv</h2>
    </div>
    <div class="box px-5 py-3 d-flex flex-wrap">
        <AppCard v-for="currentSeries in store.series" :item="currentSeries"></AppCard>
    </div>

</template>

<style>

.box{
    width: 100%;

    gap: 20px;
}


</style>