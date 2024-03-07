<script>

    import axios from 'axios';

    import search from '../components/search.vue'

    import {store} from '../store.js';

    export default {

        components: {

            search,

        },

        name: 'AppHeader',

        data() {
            return {

                store,
                
            }
        },

        methods: {

        searchFilm() {

            axios.get('https://api.themoviedb.org/3/search/movie?api_key=97743c634c9ca6743f0e8d3a08c83291&query=' + this.store.search)
                .then(res => {
                console.log(res.data.results)

                this.store.movie = res.data.results;
                });

                console.log("Ricerca percepita")
            },

        },

    }

</script>

<template>
    
    <div class="box-header px-3 ">
        <h1 class="m-0">BOOLFLIX</h1>
        <search @search="searchFilm()"></search>
    </div>

</template>

<style>

.box-header{
    width: 100%;
    height: 80px;

    display: flex;
    align-items: center;
    justify-content: space-between;

    border-bottom: 2px solid grey;

    h1{
        font-family:"Bebas Neue", sans-serif;
        color: red;
    }
}

</style>