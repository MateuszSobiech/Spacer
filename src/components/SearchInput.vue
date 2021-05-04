<template>
  <div class="searchWrapper">
    <input
      id="search"
      name="search"
      :value="value"
      @input="handleChange"
      :class="{ dark }"
    />
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
    dark: {
      type: Boolean,
      default: false,
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
  margin-bottom: 40px;
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

.dark {
  color: #171717;
  border-bottom: 1px solid #171717;
}
</style>
