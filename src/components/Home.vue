<template>
  <div>
    <p v-border:solid.round="{ width: '3px', color: 'brown' }">Home</p>
    <h2>{{ title | lowerCase | upperCase }}</h2>
    <p>{{ subTitle | upperCase | lowerCase }}</p>
    <p>{{ number }}</p>
    <button @click="number++">+1</button>
    <CountNumber></CountNumber>
  </div>
</template>

<script>
  import CountNumber from './CountNumber.vue';
  import { tokyoNumber } from '@/tokyoNumber.js';

  export default {
    mixins: [tokyoNumber],
    data() {
      return {
        mainText: 'メイン',
      };
    },
    components: {
      CountNumber,
    },
    directives: {
      border(el, binding) {
        el.style.borderWidth = binding.value.width;
        el.style.borderColor = binding.value.color;
        el.style.borderStyle = binding.arg;
        if (binding.modifiers.round) {
          el.style.borderRadius = '0.5em';
        }
      },
    },
  };
</script>
