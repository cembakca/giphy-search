<template>
  <div id="app">
    <h3>Giphy | Choose Your Favorite Gif!</h3>
    <search v-on:searchrequested="handleSearch" ></search>
    <p v-if="isLoading">loading</p>
    <preview
      v-on:savegif="saveGif"
      v-on:deletegif="deleteGif"
      v-bind:gifs="gifs"
      v-bind:saved="saved"
    ></preview>
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
      gifs: [],
      saved: []
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
    },
    saveGif(idx) {
      this.saved.push(this.gifs[idx]);
    },
    deleteGif(idx) {
      this.saved.splice(idx, 1);
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
