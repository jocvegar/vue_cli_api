<template>
  <div class="quote">
    <section v-if="errored">
      <p>No lo pude cargar! Tratá en un ratito</p>
    </section>
    <section v-else>
      <div v-if="loading" class="loading">Loading something cool...</div>
      <div v-else>
        <h3>{{ quote }}</h3>
        <button @click="getQuote" type="button">
          Another Quote Please :)
        </button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Quote',
  data() {
    return {
      quote: '',
      loading: true,
      errored: false,
    };
  },
  methods: {
    getQuote() {
      const proxyurl = 'https://cors-anywhere.herokuapp.com/';
      const url = 'https://www.affirmations.dev/'; // site that doesn’t send Access-Control-*
      fetch(proxyurl + url)
        .then((response) => response.json())
        .then(this.setResults)
        .catch((error) => {
          console.log(error);
          console.log(`Cant access ${url} response. Blocked by browser?`);
          this.errored = true;
        })
        .finally(this.loading = false);
    },
    setResults(result) {
      this.quote = result.affirmation;
      this.$emit('changeUI', this.generateRandomIndex());
    },
    generateRandomIndex() {
      return Math.floor(Math.random() * 10);
    },
  },
  created() {
    this.getQuote();
    this.generateRandomIndex();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
button {
  background-color: #41B883;
  font-size: 16px;
  padding: 14px 40px;
  border-radius: 4px;
  margin-top: 5em;
  color: white;
  border: none;
  outline:none;
}
.loading{
  padding-top:2rem;
}
</style>
