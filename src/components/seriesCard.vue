<script>

export default {

    name: 'seriesCard',
    
    props: {

        series: Object,

    },

    methods: {

        language() {

            let flag = this.series.original_language;


            switch(this.series.original_language){
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

        }
    }
}

</script>

<template>

    <div class="card">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
            <h4 class="card-title">{{ series.original_name }}</h4>
            <strong class="card-text">{{ series.name }}</strong>
            <div class="d-block ">
                <p class="m-0 d-inline">Lingua: </p>
                <img class="d-inline " :src="language(series.original_language)" alt="">
            </div>
            <p class="card-text">Voto: {{ series.vote_average }}</p>
        </div>
    </div>

</template>

<style>

</style>