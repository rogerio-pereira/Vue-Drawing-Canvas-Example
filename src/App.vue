<template>
  <div id="app">
    <!-- image.sync is important because if not model (picture) isn't updated -->
    <vue-drawing-canvas
      ref="assinatura1"
      :image.sync="picture" 
      saveAs="png"
      :styles="{
        border: 'solid 1px #000',
      }"
    /><br/>

    <button @click='save'>Save Image</button>
    <button @click.prevent="$refs.assinatura1.undo()">
      Undo
    </button>
    <button @click.prevent="$refs.assinatura1.redo()">
      Redo
    </button>
    <button @click.prevent="$refs.assinatura1.reset()">
      Reset
    </button><br/><br/>

    <img :src='picture' width='100px' alt=''/>
  </div>
</template>

<script>
import VueDrawingCanvas from 'vue-drawing-canvas';

export default {
  name: 'App',

  components: {
    VueDrawingCanvas,
  },

  data() {
    return {
      picture: null,
    };
  },

  methods: {
    save() {
      const link = document.createElement('a');
      link.download = 'image';
      link.href = this.picture;
      link.click();
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
