/* eslint-disable */ 
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
      backgroundColor: [
        '#f76a8c',
        '#f8dc88',
        '#f8fab8',
        '#ccf0e1',
        '#ffd1bd',
        '#639a67',
        '#d8ebb5',
        '#d9bf77',
        '#1eb2a6',
        '#f67575',
      ],
    };
  },
  methods: {
    changeUI(index) {
      this.image = index;
      this.backgroundColorChanger(index);
    },
    backgroundColorChanger(index) {
      const el = document.body;
      el.style.backgroundColor = this.backgroundColor[index];
    },
  },
  created() {
    this.image = 0;
    document.body.style.backgroundColor = '#fff';
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
