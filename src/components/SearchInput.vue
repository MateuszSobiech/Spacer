<template>
  <div class="searchWrapper">
    <input
      id="search"
      name="search"
      v-model="searchValue"
      @input="handleInput"
      placeholder="Moon"
    />

    <ul>
      <li v-for="item in results" :key="item.data[0].nasa_id">
        <p>{{ item.data[0].description }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'SearchInput',

  data() {
    return {
      searchValue: '',
      results: [],
    };
  },

  methods: {
    // eslint-disable-next-line func-names
    handleInput: debounce(function () {
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

<style>
.searchWrapper {
  display: flex;
  width: 300px;
  flex-direction: column;
  align-items: center;
}

input {
  margin-top: 25px;
  height: 30px;
  border: 0;
  border-bottom: 1px solid black;
  text-align: center;
  background: none;
  width: 80%;
}

::placeholder {
  color: white;
  opacity: 0.7;
  font-size: 1rem;
}
</style>
