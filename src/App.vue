<script>

import axios from 'axios';
import '@fortawesome/fontawesome-free/css/all.css';

import {store} from './store.js';

import AppNav from './components/AppNav.vue';
import AppCardItem from './components/AppCardItem.vue';

export default {
  data() {
    return {
      films: [],
      store,
    }
  },

  components: {
    AppNav,
    AppCardItem,
  },

  created() {
    axios
    .get('https://api.themoviedb.org/3/search/multi?api_key=592c7f331c0a2f4ae38ae95ab2c85d31&query=maze+runner')
    .then(res => {
      const films = res.data.results;
      films.forEach(film => {
        store.films.push(film);
      });
    console.log(store.films);
    });

  },

  methods: {
    searchFilm(searchText) {
      this.store.films = [];
      axios.get(`https://api.themoviedb.org/3/search/multi?api_key=592c7f331c0a2f4ae38ae95ab2c85d31&query=${searchText}`)
      .then(res => {
        const films = res.data.results;
        films.forEach(film => {
          store.films.push(film);
        });
      console.log(store.films);
      });
    },
  }
}

</script>

<template>
  <AppNav @search="searchFilm"></AppNav>
  <div id="container">
    <ul>
      <AppCardItem 
      v-for="currentFilm in store.films"
      :film="currentFilm"></AppCardItem>
    </ul>
  </div>
</template>

<style scoped>

#container {
  padding: 1em;

  ul {
    display: flex;
    justify-content: center;
    flex-flow: row wrap;
    gap: 2em;

    list-style: none;
  }
}


</style>
