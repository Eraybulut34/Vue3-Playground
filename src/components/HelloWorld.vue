<script>
import { ref } from "vue";
import axios from "axios";
export default {
  setup() {
    const count = ref(0);
    const url = "https://jsonplaceholder.typicode.com/posts";
    const items = null;

    return {
      items,
      url,
      count,
    };
  },

  mounted() {
    axios.get(this.url).then((response) => (this.items = response.data));
  },
};
</script>

<template>
  <div class="" v-for="item in items" :key="item.id">{{ item.id }}</div>
  <button @click="count += 100">{{ count }}</button>
</template>