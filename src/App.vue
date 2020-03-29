/* eslint-disable import/no-dynamic-require */
<template>
  <div id="app">
    <img :src="require(`./assets/${image}.png`)" alt="happy stuff"/>
    <Quote @changeUI='changeUI($event)'/>
  </div>
</template>

<script>
import Quote from './components/Quote.vue';

export default {
  name: 'App',
  components: {
    Quote,
  },
  data() {
    return {
      image: '',
    };
  },
  methods: {
    changeUI(index) {
      this.image = index;
    },
  },
  created() {
    this.image = 0;
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
img {
  width:100px;
  height:100px;
  object-fit:scale-down;
}
</style>
