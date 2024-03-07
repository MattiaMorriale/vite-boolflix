<script>

    import {store} from '../store.js';

    import movieCard from '../components/movieCard.vue'

    import seriesCard from '../components/seriesCard.vue'

    export default {

        name: 'AppMain',

        data() {
            return {

                store,

            }
        },

        components: {

            movieCard,
            seriesCard,

        }
        
    }

</script>

<template>

    <div class="box  px-3 py-3 d-flex flex-wrap ">
        <movieCard v-for="currentMovie in store.movie" :movie="currentMovie"></movieCard>
    </div>
    <div class="box px-3 pt-3 d-flex flex-wrap ">
        <seriesCard v-for="currentSeries in store.series" :series="currentSeries"></seriesCard>
    </div>

</template>

<style>

.box{
    width: 100%;

    gap: 20px;
}


</style>