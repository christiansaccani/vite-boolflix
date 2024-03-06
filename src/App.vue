<script>

import axios from 'axios';

import {store} from './store.js';

import AppNav from './components/AppNav.vue';

export default {
  data() {
    return {
      films: [],
      store,
    }
  },

  components: {
    AppNav,
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
  // ${searchText}
  methods: {
    searchFilm(searchText) {
      this.store.films = [];
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=592c7f331c0a2f4ae38ae95ab2c85d31&query=avatar`)
      .then(res => {
          console.log(res.data);
          this.store.films = res.data;
          console.log(this.store.films);
      })
      .catch(error => {
          console.error('Errore durante la ricerca delle carte:', error);
      });
    },
  }
}

</script>

<template>
  <AppNav @search="searchFilm"></AppNav>
</template>

<style scoped>

</style>
