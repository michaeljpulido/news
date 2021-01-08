<template>
  <input type="text" placeholder="Search" name="query" v-model="query" v-on:keyup.enter="onEnter">
</template>

<script>
export default {
  name: 'Search',
  props: {},
  methods: {
    onEnter() { 
        let path = document.location.origin + `?q=${this.query}`;
        history.pushState({ path: path }, `News - ${this.query}`, path);

        this.$emit('search', this.query);
    }
  }
}
</script>

<style scoped>
  input {
    border: lightgray 2px dashed;
    border-radius: 30px;
    width: 280px; 
    height: 30px; 
    padding: 5px 20px; 
    font-size: 20px; 
    font-weight: 100; color: #444;
  }

  input:focus {
    outline: none;
  }

  input:before {
    content: "\2315";
    margin-left: -24px;
  }
</style>