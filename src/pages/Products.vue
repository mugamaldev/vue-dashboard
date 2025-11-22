<template>
  <div>
    <h1>Products</h1>

    <form @submit.prevent="createProduct">
      <input v-model="name" placeholder="Name">
      <input v-model="price" placeholder="Price">
      <input v-model="stock" placeholder="Stock">
      <button>Add Product</button>
    </form>

    <table border="1" width="100%">
      <tr>
        <th>Name</th>
        <th>Price</th>
        <th>Stock</th>
        <th>Actions</th>
      </tr>

      <tr v-for="p in products" :key="p.id">
        <td>{{ p.name }}</td>
        <td>{{ p.price }}</td>
        <td>{{ p.stock }}</td>

        <td>
          <button @click="deleteProduct(p.id)">Delete</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import api from "../api/axios";

export default {
  data() {
    return {
      products: [],
      name: "",
      price: "",
      stock: "",
    };
  },

  async mounted() {
    this.fetchProducts();
  },

  methods: {
    async fetchProducts() {
      const res = await api.get("/products");
      this.products = res.data;
    },

    async createProduct() {
      await api.post("/products", {
        name: this.name,
        price: this.price,
        stock: this.stock,
      });

      this.fetchProducts();
    },

    async deleteProduct(id) {
      await api.delete(`/products/${id}`);
      this.fetchProducts();
    },
  }
};
</script>
