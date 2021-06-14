<template>
    <div class="film">
        <p>Titolo: {{item.title}}</p>
        <p>Titolo originale: {{item.original_title}}</p>
        <p>Lingua: {{item.original_language}}</p>
        <p>Voto: {{item.vote_average}}</p>
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
    }

</style>