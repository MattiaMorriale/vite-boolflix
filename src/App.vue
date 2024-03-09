<script>

  import axios from 'axios';

  import {store} from './store.js';

  import AppHeader from './components/AppHeader.vue'

  import AppMain from './components/AppMain.vue'

  export default{

    components: {

      AppHeader,
      AppMain,

    },

    data() {

      return {

        store,

      }

    },

    created() {

      axios
        .get('https://api.themoviedb.org/3/search/movie?api_key=97743c634c9ca6743f0e8d3a08c83291&query=' + this.store.search)

        .then(res => {

          this.store.movie = res.data.results

        }).catch(err => {

          console.log(err)

        })


      axios
        .get('https://api.themoviedb.org/3/search/tv?api_key=97743c634c9ca6743f0e8d3a08c83291&language=it_IT&query=' + this.store.search)

        .then(res => {

          this.store.series = res.data.results

        }).catch(err => {

          console.log(err)

        })

        axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=e99307154c6dfb0b4750f6603256716d&`)
        
        .then(res => {

        this.store.arrGen = res.data

        console.log(store.arrGen.genres);


        }).catch(err => {
          console.log(err)})
    }
  }

</script>

<template>

  <AppHeader></AppHeader>

  <AppMain></AppMain>

</template>

<style>


</style>
