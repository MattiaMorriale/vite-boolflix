<script>

    import axios from 'axios';

    import {store} from '../store.js';

    export default {

        name: 'AppHeader',

        data() {
            return {

                store,
                
            }
        },

        methods: {

            searchFilm() {

                this.store.movie = [],

                this.store.series = [],

                axios
                .get('https://api.themoviedb.org/3/search/movie?api_key=97743c634c9ca6743f0e8d3a08c83291&query=' + this.store.search)
                
                .then(res => {
                console.log(res.data.results)

                this.store.movie = res.data.results;
                });

                console.log("Ricerca percepita")
            
                axios
                .get('https://api.themoviedb.org/3/search/tv?api_key=97743c634c9ca6743f0e8d3a08c83291&language=it_IT&query=' + this.store.search)
        
                .then(res => {
        
                console.log('ricerca percepita 2')
        
                console.log(res.data.results)
        
                this.store.series = res.data.results
        
                }).catch(err => {
        
                console.log(err)
                
                })
            },
        },
    }

</script>

<template>
    
    <div class="box-header px-3 ">
        <div class="box-img">
            <img class="w-100 h-100 " src="/public/logo.png" alt="@">
        </div>
        <div>
            <div class="input-group ">
                <input type="text" class="form-control shadow-none" placeholder="Cerca" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="store.search">
                <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="searchFilm()"><i class="fa-solid fa-magnifying-glass"></i></button>
            </div>  
        </div>
    </div>

</template>

<style>

.box-header{
    width: 100%;
    height: 80px;

    background-color: black;

    position: fixed;
    top: 0;
    left: 0;

    z-index: 99;

    display: flex;
    align-items: center;
    justify-content: space-between;

    border-bottom: 2px solid grey;

    .box-img{
        height: 50px;

    }
}

</style>