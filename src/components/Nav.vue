<template>
    <nav>
        <div class="nav-logo">
            <img src="../assets/img/fabioflix-logo.png" alt="">
        </div>
        <div class="nav-search">
            <input 
            type="text"
            placeholder="Cerca un film..."
            v-model="searchedText"
            >
            <span
            class="btn"
            @click="$emit('performSearch', searchedText)">
                cerca
            </span>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'Nav',
    data: function () {
        return {
            searchedText: '',
        }
    },
}
</script>

<style lang="scss" scoped>
// variables.scss - !vanno importate per ogni componente!
@import '../style/variables.scss';

    nav {
        display: flex;
        justify-content: space-between;
        align-items: center;

        height: 75px;
        width: 100%;
        padding: 15px 30px;
        background-color: $bg-color-two;

        .nav-logo {
            height: 100%;
            img {
                height: 100%;
            }
        }

        .nav-search {
            display: flex;

            .btn {
                padding: 0 15px;
                border: 2px solid white;
                border-radius: 5px;
                margin-left: 30px;
                transition: 0.5s;

                &:hover {
                    cursor: pointer;
                    color: black;
                    background-color: white;
                    transform: scale(1.1);
                }
            }

        }
    }

</style>