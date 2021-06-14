<template>
    <nav>
        <input 
        type="text"
        placeholder="Cerca un film..."
        v-model="searchedText"
        >
        <span
        @click="$emit('performSearch', searchedText)">
            bottone
        </span>
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
        height: 75px;
        width: 100%;
        background-color: $bg-color-two;
    }

</style>