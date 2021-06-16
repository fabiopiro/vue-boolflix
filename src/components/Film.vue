<template>
    <div 
    class="film"
    v-if="item.poster_path != null"
    >
        <img 
        class="film-img"
        :src="'https://image.tmdb.org/t/p/w342/'+ item.poster_path" alt="">

        <div class="film-info">
            <p class="film-title">{{item.title}}{{item.name}}</p>
            <p
            v-if="item.title !== item.original_title"
            >
            Original Title: {{item.original_title}}</p>
           
            <p
            class="film-language"
            v-if="availableFlags.includes(item.original_language)"
            > Language:
                <img 
                    class="flag-image"
                    v-if="availableFlags.includes(item.original_language)"
                    :src="require(`../assets/img/flags/${item.original_language}.png`)" 
                    alt=""
                    >
            </p>
            <p v-else>Language: {{item.original_language}}</p>

            <!-- star rating -->
            <div class="rating">
                <i class="fa-star"
                v-for="index in 5"
                :key="index"
                :class="(index <= item.vote_average) ? 'fas' : 'far'"
                ></i>
            </div>
            <div class="overview">
                <p>{{item.overview}}</p>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'Film',
    props: ['item'],
    data: function () {
        return {
            availableFlags: ['it' , 'en'],
        }
    },

    created: function () {
        const voteRounded = Math.round((this.item.vote_average /2));
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
        background-color: $bg-color-two;
        position: relative;

        transition: 0.5s;

        border-radius: 20px;

        overflow: hidden;

        &:hover {

            transform: scale(1.05);

            .film-info {
                visibility: visible;
                transition: 0.5s;
            }
            .film-img {
                opacity: 0.3;
            }
        }

        .film-img {

            width: 100%;
            height: 100%;

            transition: 0.5s;
        }


        .film-info {

            display: flex;
            flex-direction: column;
            justify-content: space-between;
            
            text-align: center;
            width: 100%;
            height: 100%;
            padding: 30px;

            position: absolute;
            top: 0;
            left: 0;

            // visibility: hidden;

            .film-title {
                color: red;
                font-size: 30px;
                font-weight: 700;
            }

            .film-language {

                display: flex;
                justify-content: center;

                .flag-image {
                    margin-left: 5px;
                    width: 30px;
                    height: 20px;
                }
            }

        }

        .overview {
            height: 50%;
            border-top: 2px solid red;
            margin-top: 30px;
            padding: 15px;

            overflow: auto;
        }
    }

</style>