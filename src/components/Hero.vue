<template>
  <div class="heroImg" />
</template>

<script>
export default {
  name: 'Hero',
};
</script>

<style lang="scss" scoped>
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
.heroImg::after {
  content: '';
  background: rgba(0, 0, 0, 0.2);
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  width: 100%;
  height: 100vh;
}
</style>
