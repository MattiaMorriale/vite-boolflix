<script>

    import {store} from '../store.js'

    export default {

        name: 'search',

        data() {
            return {
                store,
            }
        }

    }

</script>

<template>

    <div>
        <div class="input-group ">
            <input type="text" class="form-control shadow-none" placeholder="Cerca" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="store.search">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('search')"><i class="fa-solid fa-magnifying-glass"></i></button>
        </div>  
    </div>
    
</template>

<style>

</style>