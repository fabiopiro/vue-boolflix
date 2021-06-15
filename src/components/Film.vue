<template>
    <div 
    class="film"
    v-if="item.poster_path != null"
    >
        <img 
        class="film-img"
        :src="'https://image.tmdb.org/t/p/w342/'+ item.poster_path" alt="">

        <div class="film-text">
            <p>Titolo: {{item.title}}{{item.name}}</p>

            <p
            v-if="item.title !== item.original_title"
            >
            Titolo originale: {{item.original_title}}</p>

            <p
            v-if="item.original_language == 'it'"
            >Lingua: <img class="flag" src="../assets/img/it.png" alt=""></p>
            <p
            v-else-if="item.original_language == 'en'"
            >Lingua: <img class="flag" src="../assets/img/en.png" alt=""></p>
            <p
            v-else
            >Lingua: {{item.original_language}}</p>

            <p
            v-for="index in item.vote_average"
            :key="index"
            >
                <i class="fas fa-star"></i>
            </p>

            <p>{{item.vote_average}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Film',
    props: ['item'],

    created: function () {
        const voteRounded = Math.round((this.item.vote_average /2));
        // const emptyStars = 5 - voteRounded;
        console.log(voteRounded);
        this.item.vote_average = voteRounded
    },
}
</script>

<style lang="scss" scoped>
// variables.scss - !vanno importate per ogni componente!
@import '../style/variables.scss';

    .film {
        height: 500px;
        width: 342px;

        margin: 15px;
        background-color: purple;

        position: relative;

        .film-img {
            width: 100%;
            height: 100%;
        }


        .film-text {
            height: 100%;
            width: 100%;
            position: absolute;
            top: 0;
            left: 0;

            .flag {
                width: 30px;
                height: 20px;
            }
        }
    }

</style>