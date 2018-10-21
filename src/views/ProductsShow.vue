<template>
  <div class="product-show">
    <div class="container">
      <h1>{{ product.formatted }}</h1>
    </div>
  </div>
</template>

<style>
</style>

<script>
var axios = require('axios');  
export default {
  data: function() {
    return {
      product: {
        formatted: {}
      }
    };
  },
  created: function() {
    axios
    .get("http://localhost:3000/api/products/" + this.$route.params.id)
    .then(response => {
      this.product = response.data;
    });
  },
  methods: {},
  computed: {}
};
</script>