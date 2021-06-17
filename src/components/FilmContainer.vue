<template>
    <div>
        <!-- nav - component -->
        <Nav 
        @performSearch="searchMovie"
        />
        <!-- /nav  component-->
        <!-- welcome & error message -->
        <h1
        v-if="this.movies.length == 0 && this.query.length == 0">
        Cerca un film o una serie...
        </h1>
        <h1
        v-else-if="this.query.length > 0 && this.movies.length == 0"
        >
        Non hai trovato nulla...riprova
        </h1>
        <!-- /welcome & error message -->
        <!-- film section -->
        <section class="container">
            <Film 
            v-for="movie in movies"
            :key="movie.id"
            :item="movie"
            />
        </section>
        <!-- /film section -->
    </div>
</template>

<script>
import Nav from './Nav.vue'
import Film from './Film.vue'

// axios
import axios from 'axios';

export default {

    name: 'FilmContainer',
    components: {
        Nav,
        Film,
    },

    data: function () {
        return {

            movies:[],

            // api movie
            apiUrlMovie: 'https://api.themoviedb.org/3/search/movie',
            // api serie
            apiUrlSerie: 'https://api.themoviedb.org/3/search/tv',
            // api my key - themoviedb.org
            myKey: '8473eea95ee5c9fdf429845509201140',
            // film/serie to search - required
            query: '',
        }
    },
    methods: {
        searchMovie: function (text) {

            this.query = text;
            // console.log(this.query);

            axios.all(
                [
                axios.get(this.apiUrlMovie, {
                    params: {
                        api_key: this.myKey,
                        query: this.query,
                    }
                }),
                axios.get(this.apiUrlSerie, {
                    params: {
                        api_key: this.myKey,
                        query: this.query,
                    }
                })
                ]
            )
            .then (
                axios.spread((...response) => {
                
                const resone = response[0].data.results
                const restwo = response[1].data.results

                this.movies = resone.concat(restwo)

                }
            ))

        }
    },
}
</script>

<style lang="scss" scoped>

    h1 {
        font-size: 50px;
        position: absolute;
        top: 50%;
        left: 30%;
        // transform: translate(-50% , -50%);
        animation-name: bigAndSmall;
        animation-duration: 3s;
        animation-iteration-count: infinite;

        @keyframes bigAndSmall {
            0%{transform: scale(1.0);}
            50% {transform: scale(1.5);}
            100% {transform: scale(1.0);}
        }
    }

    .container {
        display: flex;
        flex-wrap: wrap;
    }

</style>