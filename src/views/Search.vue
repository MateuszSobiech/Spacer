<template>
  <div class="wrapper">
    <Claim />
    <SearchInput />
  </div>
</template>

<script>
// @ is an alias to /src
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

export default {
  components: { Claim, SearchInput },

  name: 'Search',

};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  height: 100vh;
  background-image: url('../../img/hero.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0%;
}
</style>
