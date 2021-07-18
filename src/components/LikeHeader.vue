<template>
  <header>
    <slot name="title" :user="user"></slot>
    <slot></slot>
    <hr />
    <h1>トータルのいいね数</h1>
    <slot name="number"></slot>
  </header>
</template>

<script>
  export default {
    data() {
      return {
        user: {
          firsetName: 'Jack',
          lastName: 'Donald',
        },
      };
    },
  };
</script>
