<template>
  <div>
    <button @click="getData">Get Data</button>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      items: []
    }
  },
  methods: {
    getData() {
      axios.get('https://api.publicapis.org/entries')
        .then(response => {
          console.log(response.data)
          this.items = response.data.entries;
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
}
</script>
