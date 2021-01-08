<template>
  <Header />
  <main>
    <Search @search="search" />
    <Articles v-bind:articles="articles" @imageClicked="imageClicked" />
  </main>
  <Modal v-bind:src="src" v-show="src" @modalClicked="modalClicked" />
  <Footer />
</template>

<script>
import Articles from './components/Articles.vue'
import Header from './components/Header.vue'
import Search from './components/Search.vue'
import Modal from './components/Modal.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header, Search, Articles, Modal, Footer
  },
  data() {
    return {
      articles: [],
      src: ''
    }
  },
  methods: {
    search (query) {
      let _this = this;
      fetch(`https://newsapi.org/v2/everything?q=${query}&apiKey=036872dcffa143318b7be570289af938`)
        .then(res => res.json())
        .then(data => {
          _this.articles = data.articles;
          document.title = `Today's News - ${query}`;
        });
    },
    imageClicked (src) {
      this.src = src;
    },
    modalClicked() {
      this.src = '';
    }
  },
  created() {
    document.title = `Today's News`;
  },
  mounted() {
    let query = new URLSearchParams(window.location.search).get('q');
    if (query) {
      this.search(query);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
