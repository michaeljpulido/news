<template>
  <div v-on:click="modalClicked">
      <img :src=src>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    src: String
  },
  methods: {
    modalClicked() {
      this.$emit('modalClicked');
    }
  }
}
</script>

<style scoped>
  div {
    position: fixed; top: 0; right: 0; bottom: 0; left: 0;
    background-color: rgb(0, 0, 0, .9);
    display: flex;
    justify-content: center;
    align-items: center;

  }
  img {
    padding: 50px;
    max-width: 100%;
    max-height: 100%;
  }
</style>