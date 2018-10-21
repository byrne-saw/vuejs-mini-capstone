<template>
  <div class="products-new">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>Create a Product</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Name:</label> 
          <input type="text" class="form-control" v-model="name">
        </div>
        <div class="form-group">
          <label>Description:</label>
          <input type="text" class="form-control" v-model="description">
        </div>
        <div class="form-group">
          <label>Price:</label>
          <input type="text" class="form-control" v-model="price">
        </div>
        <div class="form-group">
          <label>Supplier_ID:</label>
          <input type="text" class="form-control" v-model="supplier_id">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      name: "",
      description: "",
      price: "",
      supplier_id: ""
    };
  },
  methods: {
    submit: function() {
      var params = {
        name: this.name,
        description: this.description,
        price: this.price,
        supplier_id: this.supplier_id
      };
      axios
        .post("http://localhost:3000/api/products", params)
        .then(response => {
          this.$router.push("/products/" + response.data.id);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>