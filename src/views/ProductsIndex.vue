<template>
  <div class="products-index">
    <div class="containter">
      <h1>Products</h1>

      <div v-for="product in products">
        <h2>{{ product.name }}</h2>
        <p>Description: {{ product.description }}</p>
        <p>Price: {{ product.formatted.price }}</p>
        <p>Tax: {{ product.formatted.tax }}</p>
        <p>Total {{ product.formatted.total }}</p>
     </div>
      
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
      products: []
    };
  },
  created: function() {
    console.log(localStorage["jwt"]);
    axios
    .get("http://localhost:3000/api/products")
    .then(response => {
      this.products = response.data;
    });
  },
  methods: {},
  computed: {}
};
</script>