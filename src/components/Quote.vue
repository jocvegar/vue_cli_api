<template>
  <div class="quote">
    <h3>{{ quote }}</h3>
    <button @click="getQuote" type="button">
      Another Quote Please :)
    </button>
  </div>
</template>

<script>
export default {
  name: 'Quote',
  data() {
    return {
      quote: '',
    };
  },
  methods: {
    getQuote() {
      const proxyurl = 'https://cors-anywhere.herokuapp.com/';
      const url = 'https://www.affirmations.dev/'; // site that doesn’t send Access-Control-*
      fetch(proxyurl + url)
        .then((response) => response.json())
        .then(this.setResults)
        .catch(() => console.log(`Cant access ${url} response. Blocked by browser?`));
    },
    setResults(result) {
      this.quote = result.affirmation;
    },
  },

  created() {
    this.getQuote();
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
}

</style>
