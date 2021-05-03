<template>
  <div id="app">
    <div class="wrapper">
      <Hero />
      <Claim />
      <SearchInput v-model="searchValue" @input="handleInput" />
    </div>
  </div>
</template>

<script>
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Hero from '@/components/Hero.vue';
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  components: { Claim, SearchInput, Hero },

  name: 'App',

  data() {
    return {
      searchValue: '',
    };
  },

  methods: {
    // eslint-disable-next-line func-names
    handleInput: debounce(function () {
      console.log(this.searchValue);
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((res) => {
          this.results = res.data.collection.items;
        })
        .catch((e) => {
          console.log(e);
        });
    }, 500),
  },
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

.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  height: 100vh;
}
</style>
