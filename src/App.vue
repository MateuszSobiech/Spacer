<template>
  <div id="app">
    <div :class="[{ flexStart: step === 1 }, 'wrapper']">
      <transition name="fade">
        <Hero v-if="step === 0" />
      </transition>
      <Claim v-if="step === 0" />
      <SearchInput
        v-model="searchValue"
        @input="handleInput"
        :dark="step === 1"
      />
      <div class="results" v-if="results && !loading && step === 1">
        <Item
          v-for="item in results"
          :item="item"
          :key="item.data[0].nasa_id"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Hero from '@/components/Hero.vue';
import Item from '@/components/Item.vue';
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {

  components: {
    Claim, SearchInput, Hero, Item,
  },

  name: 'App',

  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },

  methods: {
    // eslint-disable-next-line func-names
    handleInput: debounce(function () {
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((res) => {
          this.results = res.data.collection.items;
          this.loading = false;
          this.step = 1;
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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-out;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
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

  &.flexStart {
    justify-content: start;
  }
}

.results {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;

  @media (min-width: 768px) {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>
