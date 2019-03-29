<template>
  <div class="preview">
    <div class="gif" v-for="gif in gifs">
      <img :src="gif.images.fixed_height.url" />
    </div>
  </div>
</template>


<script>
export default {
  props: [ 'gifs' ]
}
</script>

<style>
  .preview {
    display: flex;
    width: 100%;
    height: 100%;
    flex-wrap: wrap;
    overflow-y: auto; 
  }

  .gif {
    flex-grow: 1;
    flex-shrink: 0;
    margin: 0 10px;
  };
</style>

