<script>

export default {

    name: 'movieCard',

    props: {

        movie: Object,

    },

}

</script>

<template>

    <div class="card">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
            <h4 class="card-title">{{ movie.original_title }}</h4>
            <strong class="card-text">{{ movie.title }}</strong>
            <p class="card-text">Lingua: {{ movie.original_language }}</p>
            <p class="card-text">Voto: {{ movie.vote_average }}</p>
        </div>
    </div>

</template>

<style>

.card {
    width: calc(100% / 5 - 20px / 5 * 4);
}

</style>