<template>
  <div class="panel">
    <h1 v-if="title" class="title">{{ title }}</h1>
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'dash-panel',
    props: {
      title: ''
    }
  }
</script>

<style scoped>
  h1 {
    margin: 0;
  }

  .title {
    background-color: #eee;
  }
</style>
