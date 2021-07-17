<template>
  <article>
    <LikeHeader></LikeHeader>
    <h2>{{ number }}</h2>
    <LikeNumber
      :total-number="number"
      @my-click="incrementNumber($event)"
    ></LikeNumber>
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
    methods: {
      incrementNumber(value) {
        this.number = value;
      },
    },
  };
</script>

<style lang="scss" scoped>
  article {
    border: 1px solid blue;
  }
</style>
