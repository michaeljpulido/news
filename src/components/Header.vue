<template>
  <header>
    <h1>Today's News</h1>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {}
}
</script>

<style scoped>
  h1 { font-weight: 100; font-size: 60px; }

  @media (max-width: 600px) {
    h1 { font-size: 40px; margin: 20px 0; }
  }
</style>