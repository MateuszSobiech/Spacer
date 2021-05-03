<template>
  <img class="heroImg" />
</template>

<script>
export default {
  name: 'Hero',
};
</script>

<style>
.heroImg {
  width: 100%;
  min-height: 100vh;
  position: fixed;
  top: 0;
  background-image: url('../../img/hero.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0%;
  z-index: -1;
}
</style>
