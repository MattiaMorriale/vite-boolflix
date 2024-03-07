<script>

export default {

    name: 'movieCard',

    props: {

        movie: Object,

    },

    methods: {
        language(lingua) {
            
            return `https://flagcdn.com/16x12/${lingua}.png`

        }
    }

}

</script>

<template>

    <div class="card">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
            <h4 class="card-title">{{ movie.original_title }}</h4>
            <strong class="card-text">{{ movie.title }}</strong>
            <div class="d-block ">
                <p class="m-0 d-inline">Lingua: </p>
                <img class="d-inline " :src="language(movie.original_language)" alt="@">
            </div>
            <p class="card-text">Voto: {{ movie.vote_average }}</p>
        </div>
    </div>

</template>

<style>

.card {
    width: calc(100% / 5 - 20px / 5 * 4);
}

</style>