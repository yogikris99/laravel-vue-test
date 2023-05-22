<template>
  <div>
      <table class="table">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Name</th>
              <th scope="col">Type</th>
              <th scope="col">Brand</th>
              <th scope="col">Actions</th>
            </tr>
          </thead>
          <tbody>
              <tr v-for="(product, index) in products" :key="product.id">
                  <td>{{ index+1 }}</td>
                  <td>{{ product.name }}</td>
                  <td>{{ product.type }}</td>
                  <td>{{ product.brand }}</td>
                  <td>
                    <div class="row gap-3">
                      <router-link :to="`/products/${product.id}/edit`" class="p-2 col border btn btn-success">Edit</router-link>
                      <button @click="deleteProduct(product.id)" type="button" class="p-2 col border btn btn-danger">Delete</button>
                    </div>
                  </td>
              </tr>
          </tbody>
      </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      products: []
    }
  },
  async created() {
    try {
      const response = await axios.get('/api/products');
      this.products = response.data;
    } catch (error) {
      console.error(error);
    }
  },
  methods: {
    async deleteProduct(id) {
      try {
        await axios.delete(`/api/products/${id}`);
        this.products = this.products.filter(product => product.id !== id);
      } catch (error) {
        console.error(error);
      }
    }
  }
}
</script>