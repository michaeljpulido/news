<template>
  <div id="articles">
    <article v-for="(article, index) in articles" v-bind:key="index" v-bind:article="article">
      <img :src=article.urlToImage v-on:click="imageClicked(article.urlToImage)">
      <div>
        <h3><a :href=article.url>{{ article.title }}</a></h3>
        <div>
          <div class="author"><span>By {{ article.author }}</span></div>
          <div class="description"><span>{{ article.description }}</span></div>
        </div>
      </div>
    </article>
  </div>
</template>

<script>

export default {
  name: 'Articles',
  props: {
    articles: Array
  },
  methods: {
    imageClicked(src) {
      this.$emit('imageClicked', src);
    }
  }
}
</script>

<style scoped>
  #articles { padding: 50px; }
  article { text-align: left; padding: 25px 0 ; overflow: auto; border-bottom: 1px lightgray solid; }
  img { width: 250px; float: left; }
  img:hover { cursor: pointer; }
  article > div { margin-left: 280px; }
  a { text-decoration: none; color: steelblue; }
  h3 { margin: 0 0 5px; }
  .author { font-style: italic; color: #666; margin-bottom: 10px; }

  @media (max-width: 768px) {
    #articles { padding: 30px; }
    article { padding: 20px 0; font-size: 15px;}
    img { width: 200px; }
    article > div { margin-left: 225px; }
  }

  @media (max-width: 600px) {
    #articles { padding: 15px 10px; }
    article { padding: 20px 0; font-size: 14px;}
    img { width: 150px; }
    article > div { margin-left: 170px; }
  }
</style>