<template>
  <div>
    <h1>Orders</h1>

    <table border="1" width="100%">
      <tr>
        <th>#</th>
        <th>Total</th>
        <th>Address</th>
        <th>Phone</th>
        <th>Items</th>
      </tr>

      <tr v-for="o in orders" :key="o.id">
        <td>{{ o.id }}</td>
        <td>{{ o.total }}</td>
        <td>{{ o.address }}</td>
        <td>{{ o.phone }}</td>
        <td>
          <ul>
            <li v-for="i in o.items" :key="i.id">
              {{ i.name }} (x{{ i.quantity }})
            </li>
          </ul>
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
      orders: []
    };
  },

  async mounted() {
    const res = await api.get("/orders");
    this.orders = res.data;
  }
};
</script>
