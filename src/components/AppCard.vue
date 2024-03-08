<script>

import axios from 'axios';

import {store} from '../store.js';

export default {

    data() {
        return {
            store,
        }
    },

    name: 'AppCard',

    props: {

        item: Object,

    },

    methods: {

        languageMovie() {

            let flag = this.item.original_language;


            switch(this.item.original_language){
            case "ja":
                flag = "jp";
                break;
            case "en":
                flag = "us";
                break;
            case "ko":
                flag = "kr";
                break;
            case "da":
                flag = "dk";
                break;
            case "zh":
                flag = "cn";
                break;
            case "cs":
                flag = "cz"
                break;
            case "uk":
                flag = "gb"
                break;
            case "hi":
                flag = "in"
                break;
            case "sv":
                flag = "se"
                break;
            default:
            }

            return `https://flagcdn.com/16x12/${flag}.png`

        },

        movieImage(img) {

            return `https://image.tmdb.org/t/p/w1280${img}`

        },

        getCast(id) {

            axios
            .get(`https://api.themoviedb.org/3/movie/${id}/credits?api_key=97743c634c9ca6743f0e8d3a08c83291`)

            .then(res => {

            console.log('ricerca percepita 3')

            console.log(res.data.cast)

            this.store.cast = res.data.cast

            this.store.cast.splice(5, store.cast.length)

            }).catch(err => {

            console.log(err)

            })


        },

        starsVote() {

            let vote = Math.round(this.item.vote_average / 2);

            let stars = [];

            for (let i = 0; i < vote; i ++) {
                
                stars.push('fa-solid fa-star')

            }

            for (let j = vote; j < 5; j++) {

                stars.push('fa-regular fa-star')

            }

            return stars

        }
    
    }
        
}



</script>

<template>

    <!--                       _      
                     (_)     
 _ __ ___   _____   ___  ___ 
| '_ ` _ \ / _ \ \ / / |/ _ \
| | | | | | (_) \ V /| |  __/
|_| |_| |_|\___/ \_/ |_|\___|
                             
                              -->

    <div class="card border-0" @click=getCast(item.id)>
        <div class="content">
            <div class="front">
                <div class="box-img">
                    <img  :src="movieImage(item.poster_path)" class="card-img-top h-100 rounded-2 ">
                </div>
            </div>
            <div class="back">
                <div class="card-body">
                    <h4 class="card-title">{{ item.original_title }}</h4>
                    <strong class="card-text">{{ item.title }}</strong>
                <div class="d-block ">
                    <p class="m-0 d-inline">Lingua: </p>
                    <img class="d-inline " :src="languageMovie(item.original_language)" alt="">
                </div>
                    <p class="card-text" >Voto: <i v-for="stars in starsVote()" :class="stars"></i>
                    </p>
                    <div class="">
                        <span v-for="currentCast in store.cast">{{ currentCast.name }}, </span>
                    </div>
                </div>
            </div>
        </div>
    </div>


</template>

<style>

.card {
    width: calc(100% / 5 - 20px / 5 * 4);
    height: 400px;

    .box-img{
        height: 400px;
    }
}

.content {
  
    box-shadow: 0 0 15px rgba(0,0,0,0.1);

    transition: transform 1s;
    transform-style: preserve-3d;
}

.card:hover .content {
    transform: rotateY( 180deg ) ;
    transition: transform 0.5s;
}

.front,
.back {
    position: absolute;
    height: 100%;
    width: 100%;
    background: white;
    border-radius: 5px;
    backface-visibility: hidden;
}

.back {
    border: 2px solid gray;
    color: white;
    transform: rotateY( 180deg );
}

</style>