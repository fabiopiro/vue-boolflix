<template>
    <nav>
        <input type="text">
        <span>
            bottone
        </span>
    </nav>
</template>

<script>
export default {
    name: 'Nav'
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