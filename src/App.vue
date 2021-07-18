<template>
  <article>
    <LikeHeader>
      <h2>みなさん</h2>
      <template #title="slotProps">
        <h2>こんにちわ</h2>
        <p>{{ slotProps }}</p>
      </template>
      <h3>はじめまして</h3>
      <p>よろしくお願いします</p>
      <template #number>
        <h2>{{ number }}</h2>
      </template>
    </LikeHeader>

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
