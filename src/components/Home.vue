<template>
  <div>
    <p v-border:solid.round="{ width: '3px', color: 'brown' }">Home</p>
    <h2>{{ title | lowerCase | upperCase }}</h2>
    <p>{{ subTitle | upperCase | lowerCase }}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        title: 'Welcome to Tokyo',
        subTitle: 'Tokyo is a great city',
      };
    },
    filters: {
      lowerCase(value) {
        return value.toLowerCase();
      },
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
