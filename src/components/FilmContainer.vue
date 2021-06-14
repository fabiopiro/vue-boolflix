<template>
  <div>
      <Nav />

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

            // api
            apiUrl: 'https://api.themoviedb.org/3/search/movie',
            myKey: '8473eea95ee5c9fdf429845509201140',
            queryProva: 'amore',
        }
    },
    created: function () {
        axios
            .get(this.apiUrl, {
                params: {
                    api_key: this.myKey,
                    query: this.queryProva,
                }
            })
            .then (
                (response) => {
                    // console.log(response);
                    this.movies = response.data.results;
                    console.log(this.movies);
                }
            )
    }
}
</script>

<style lang="scss" scoped>

    .container {
        display: flex;
        flex-wrap: wrap;
        background-color: pink;
    }

</style>