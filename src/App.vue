<script>

  import axios from 'axios';

  import {store} from '../src/store';

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
        .get('https://api.themoviedb.org/3/search/movie?api_key=97743c634c9ca6743f0e8d3a08c83291&query=Titanic')

        .then(res => {

          console.log('ricerca percepita')

          console.log(res.data.results)

          this.store.movie = res.data

        }).catch(err => {

          console.log(err)

        })
      }
  }

</script>

<template>

  <AppHeader></AppHeader>

  <AppMain></AppMain>

</template>

<style>

</style>
