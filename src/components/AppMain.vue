<script>

    import {store} from '../store.js';

    import movieCard from '../components/movieCard.vue'

    export default {

        name: 'AppMain',

        data() {
            return {

                store,

            }
        },

        components: {

            movieCard,

        }
        
    }

</script>

<template>

    <div class="box-card px-3 pt-3 d-flex flex-wrap ">
        <movieCard v-for="currentMovie in store.movie" :movie="currentMovie"></movieCard>
    </div>

</template>

<style>

.box-card{
    width: 100%;

    gap: 20px;
}

</style>