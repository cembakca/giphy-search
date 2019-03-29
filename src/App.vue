<template>
  <div id="app">
    <search v-on:searchrequested="handleSearch" ></search>
    <p v-if="isLoading">loading</p>
    <preview v-bind:gifs="gifs"></preview>
  </div>
</template>

<script>
import Search from './components/Search.vue';
import Preview from './components/Preview.vue';

import API_KEY from './config';

export default {
  name: 'app',
  components: { Search, Preview },
  data() {
    return {
      isLoading: true,
      gifs: []
    }
  },
  methods: {
    doQuery(url) {
      fetch(url)
      .then((res) => { return res.json() })
      .then((res) => {
        this.gifs = res.data;
        this.isLoading = false;
      });
    },
    handleSearch(query) {
      this.gifs = [];
      this.isLoading = true;
      const url = `http://api.giphy.com/v1/gifs/search?q=${query}&api_key=${API_KEY}`;
      this.doQuery(url);
    }
  },
  created() {
    const url = `http://api.giphy.com/v1/gifs/trending?api_key=${API_KEY}`;
    this.doQuery(url);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
 
</style>
