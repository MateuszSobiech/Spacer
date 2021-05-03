<template>
  <div class="searchWrapper">
    <input id="search" name="search" :value="value" @input="handleChange" />
    <!-- v-model="searchValue"
      @input="handleInput"
      placeholder="Moon"
    <ul>
      <li v-for="item in results" :key="item.data[0].nasa_id">
        <p>{{ item.data[0].description }}</p>
      </li>
    </ul> -->
  </div>
</template>

<script>
export default {
  name: 'SearchInput',

  props: {
    value: {
      type: String,
      required: true,
    },
  },

  methods: {

    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style scoped>
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
  border-bottom: 1px solid white;
  color: white;
  text-align: center;
  background: none;
  width: 80%;
}

input:focus {
  outline: none;
}

::placeholder {
  color: white;
  opacity: 0.7;
  font-size: 1rem;
}
</style>
