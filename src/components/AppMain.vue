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

        },

        methods: {

            findGenres () {

                const arr = [];

                const array = store.movie.concat(store.series);

                array.forEach(element => {
                    
                    arr.push(element.genre_ids)

                });
                
                const fullArrGen = [];

                arr.forEach(element => {

                    for(let i = 0; i < element.length; i++)

                    if(!fullArrGen.includes(element[i]))

                    fullArrGen.push(element[i])

                });

                console.log(fullArrGen)

                const toto = []; 
                
                store.arrGen.genres.forEach(element => {


                    for(let j = 0; j < element.length; j++) {

                        console.log(element[j])

                        if(fullArrGen.includes(element[j].id)) {    

                            element[j].name.push(toto)

                        }
                        


                    }



                })

                console.log(toto)

                return fullArrGen

            }

        }
        
    }

</script>

<template>
        <div class="d-flex justify-content-center w-100 flex-column align-items-center ">
            <div class="py-4 w-75 d-flex justify-content-between  movie" v-if="store.movie.length != 0">
                <h2>Film</h2>
                <select id="select" @search="findGenres ()">
                    <option  value="">Cerca per genere:</option>
                    <option v-for="currentGen in findGenres()">{{ currentGen }}</option>
                </select>
            </div>
            <div class="w-100 d-flex justify-content-center ">
                <div class="box px-5 py-3 d-flex flex-wrap">
                    <AppCard v-for="currentMovie in store.movie" :item="currentMovie"></AppCard>
                </div>
            </div>
            <div class="py-4 w-75  d-flex justify-content-start" v-if="store.series.length!= 0">
                <h2>Serie Tv</h2>
            </div>
            <div class="w-100 d-flex justify-content-center ">
                <div class="box px-5 py-3 d-flex flex-wrap">
                    <AppCard v-for="currentSeries in store.series" :item="currentSeries"></AppCard>
                </div>
            </div>
        </div>


</template>

<style>

.movie{
    margin-top: 80px;
}

.box{
    width: 80%;

    gap: 20px;
}


</style>