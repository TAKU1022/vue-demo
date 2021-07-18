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

    <button @click="changeComponent('Home')">Home</button>
    <button @click="changeComponent('About')">About</button>

    <keep-alive>
      <component :is="currentComponent"></component>
    </keep-alive>
  </article>
</template>

<script>
  import LikeHeader from './components/LikeHeader.vue';
  import Home from './components/Home.vue';
  import About from './components/About.vue';

  export default {
    data() {
      return {
        number: 10,
        currentComponent: 'Home',
      };
    },
    components: {
      LikeHeader,
      Home,
      About,
    },
    methods: {
      incrementNumber(value) {
        this.number = value;
      },
      changeComponent(compornent) {
        this.currentComponent = compornent;
      },
    },
  };
</script>

<style lang="scss" scoped>
  article {
    border: 1px solid blue;
  }
</style>
