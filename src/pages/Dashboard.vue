<template>
  <div>
    <h1>Dashboard</h1>

    <div class="stats">
      <div class="stat-box">
        <h3>Total Products</h3>
        <p>{{ products }}</p>
      </div>

      <div class="stat-box">
        <h3>Total Orders</h3>
        <p>{{ orders }}</p>
      </div>
    </div>

  </div>
</template>

<script>
import api from "../api/axios";

export default {
  data() {
    return {
      products: 0,
      orders: 0,
    };
  },

  async mounted() {
    const p = await api.get("/products");
    const o = await api.get("/orders");

    this.products = p.data.length;
    this.orders = o.data.length;
  }
};
</script>
