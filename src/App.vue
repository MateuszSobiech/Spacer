<template>
  <div id="app">
    <Search />
  </div>
</template>

<script>
import Search from '@/views/Search.vue';

export default {
  components: { Search },

  name: 'App',
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Montserrat, sans-serif;
}
</style>
