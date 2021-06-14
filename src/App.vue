<template>
  <div id="app">

    <FilmContainer />

  </div>
</template>

<script>

import FilmContainer from './components/FilmContainer.vue';

export default {
  name: 'App',
  components: {
    FilmContainer,
  }
}
</script>

<style lang="scss">
  // general.scss
  @import './style/general.scss';

  // variables.scss - !vanno importate per ogni componente!
  @import './style/variables.scss';

</style>
