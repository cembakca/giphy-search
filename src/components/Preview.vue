<template>
  <div class="preview">
    <div v-if="saved.length" class="wrapper line">
      <div class="gif" v-for="(gif, idx) in saved">
        <img class="image" :src="gif.images.fixed_height.url" />
        <button class="btn deleteBtn" v-on:click="deleteGif(idx)" >Delete</button>
      </div>
    </div>
    <div class="wrapper">
      <div class="gif" v-for="(gif, idx) in gifs">
        <img class="image" :src="gif.images.fixed_height.url" />
        <button class="btn saveBtn" v-on:click="saveGif(idx)" >Save</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: [ 'gifs', 'saved' ],
  methods: {
    saveGif(idx) {
      this.$emit('savegif', idx);
    },
    deleteGif(idx) {
      this.$emit('deletegif', idx);
    }
  }
}
</script>

<style>
  .preview {
    display: flex;
    flex-direction: column;
  }

  .wrapper {
    display: flex;
    width: 100%;
    height: 100%;
    margin: 10px 0;
    flex-wrap: wrap;
    overflow-y: auto; 
  }

  .line {
    margin: 10px 0;
    border-bottom: 1px solid #ddd;
  }

  .image {
    width: 100%;
    background-position: center;
    object-fit: cover;
  }

  .gif {
    position: relative;
    flex-shrink: 0;
    margin: 0 10px;
  }

  .saveBtn {
    position: absolute;
    height: 20px;
    top: 0;
    right: 0;
    font-size: 12px;
    background-color: #06ad06;
  }
  .saveBtn:hover {
    background-color: #33be33;
  }

  .deleteBtn {
    position: absolute;
    height: 20px;
    top: 0;
    right: 0;
    font-size: 12px;
    background-color: #ff0000;
  }
  .deleteBtn:hover {
    background-color: #db3535;
  }
</style>

