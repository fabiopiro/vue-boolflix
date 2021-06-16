<template>
  <div>
      <Nav 
      @performSearch="searchMovie"
      />

      <section class="container">
        <Film 
        v-for="movie in movies"
        :key="movie.id"
        :item="movie"
        />
      </section>
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

    .container {
        display: flex;
        flex-wrap: wrap;
    }

</style>