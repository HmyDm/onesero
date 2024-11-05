<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
  export default {
    name: 'App',
    mounted() {
      document.title = '监控管理页面';
    },
  }
</script>

<style scoped>

</style>
