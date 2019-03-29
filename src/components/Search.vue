<template>
  <div class="search">
    <input class="input" type="text" v-model="query" @keypress.enter="handleSearch" />
    <button class="btn" v-on:click="handleSearch" >Search</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: ''
    }
  },
  methods: {
    handleSearch() {
      this.$emit('searchrequested', this.query);
    }
  }
}
</script>

<style>
  .search {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }

  .input {
    width: 310px;
    height: 50px;
    padding: 0 15px;
    margin-right: 20px;
    font-size: 16px;
    letter-spacing: -0.3px;
    color: #2b3d54;
    border-radius: 3px;
    outline: none;
    background-color: #ffffff;
    border: 1px solid #c5cdd7;
    -webkit-appearance: none;
  }

  .input:focus {
    border: solid 1px #007eff;
  }

  .btn {
    display: inline-block;
    height: 50px;
    padding: 0 20px;
    color: #ffffff;
    text-align: center;
    font-size: 14px;
    text-decoration: none;
    background-color: #007eff;
    border-radius: 3px;
    box-shadow: 0 1px 3px 0 rgba(3, 90, 180, 0.5);
    outline: none;
    touch-action: manipulation;
    cursor: pointer;
    user-select: none;
    background-image: none;
    font-family: 'Overpass', sans-serif;
    border: 1px solid transparent;
    transition: all .4s;
  }

  .btn:hover {
    background-color: #0568cc;
  }
</style>

