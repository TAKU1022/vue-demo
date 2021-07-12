<template>
  <article>
    <LikeHeader></LikeHeader>
    <h2>{{ number }}</h2>
    <LikeNumber></LikeNumber>
    <LikeNumber :total-number="number"></LikeNumber>
  </article>
</template>

<script>
  import LikeHeader from './components/LikeHeader.vue';

  export default {
    data() {
      return {
        number: 10,
      };
    },
    components: {
      LikeHeader,
    },
  };
</script>

<style lang="scss" scoped>
  article {
    border: 1px solid blue;
  }
</style>
