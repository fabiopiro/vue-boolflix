<template>
    <div class="film">
        <div class="film-text">
            <p>Titolo: {{item.title}}</p>
            <p
            v-if="item.title !== item.original_title"
            >Titolo originale: {{item.original_title}}</p>
            <p>Lingua: {{item.original_language}}</p>
            <p>Voto: {{item.vote_average}}</p>
        </div>
        <div class="film-image">
            <img src="https://image.tmdb.org/t/p/w342/sL0Ay3GQZRup2xOPkL63qujgzgh.jpg" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Film',
    props: ['item']
}
</script>

<style lang="scss" scoped>
// variables.scss - !vanno importate per ogni componente!
@import '../style/variables.scss';

    .film {
        height: 513px;
        width: 342px;

        margin: 15px;
        background-color: purple;

        .film-image {
            z-index: 1;
            visibility: hidden;
        }
    }

</style>