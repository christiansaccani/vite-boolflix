<script>

import axios from 'axios';

import {store} from './store.js';

export default {
  data() {
    return {
      films: [],
      store,
    }
  },

  components: {

  },

  created() {
    axios
    .get('https://api.themoviedb.org/3/search/movie?&query=maze+runner') //tolgo momentaneamente la key protetta
    .then(res => {
      const films = res.data.results;
      films.forEach(film => {
        store.films.push(film);
      });
    console.log(store.films);
    });

  },

  methods: {


  },
}

</script>

<template>

</template>

<style scoped>

</style>
