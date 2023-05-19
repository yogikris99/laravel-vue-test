<template>
  <div>
    <h2 v-if="isNewProduct">Add Product</h2>
    <h2 v-else>Edit Product</h2>
      <form @submit.prevent="submitForm">
        <div class="mb-3">
          <label for="name" class="form-label">Nama Produk:</label>
          <input class="form-control" type="text" id="name" v-model="product.name" required />
        </div>
        <div class="mb-3">
          <label class="control-label" for="radio-btn">Tipe Produk:</label>
          <div id="radio-btn">
            <div class="form-check form-check-inline">
              <label class="form-check-label">
                <input class="form-check-input" type="radio" value="Shoes" v-model="product.type" required/> Shoes
              </label>
            </div>

            <div class="form-check form-check-inline">
              <label class="form-check-label">
                <input class="form-check-input" type="radio" value="Apparel" v-model="product.type" /> Apparel
              </label>
            </div>

            <div class="form-check form-check-inline">
              <label class="form-check-label">
                <input class="form-check-input" type="radio" value="Accessories" v-model="product.type" /> Accessories
              </label>
            </div>
          </div>
        </div>
        <div class="mb-3">
          <label for="brand" class="form-label">Brand:</label>

          <select id="brand" class="form-select" v-model="product.brand" required>
            <option disabled value="">Pilih Brand</option>
            <option value="Specs">Specs</option>
            <option value="Piero">Piero</option>
            <option value="Mizuno">Mizuno</option>
            <option value="Nike">Nike</option>
            <option value="Adidas">Adidas</option>
          </select>
        </div>
        <button type="submit" v-if="isNewProduct" class="btn btn-primary">Add Product</button>
        <button type="submit" v-else class="btn btn-primary">Update Product</button>
      </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      product: {
        name: '',
        type: '',
        brand: ''
      }
    }
  },
  computed: {
    isNewProduct() {
      return !this.$route.path.includes('edit');
    }
  },
  async created() {
    if (!this.isNewProduct) {
      const response = await axios.get(`/api/products/${this.$route.params.id}`);
      this.product = response.data;
    }
  },
  methods: {
    async submitForm() {
      try {
        if (this.isNewProduct) {
          await axios.post('/api/products', this.product);
        } else {
          await axios.put(`/api/products/${this.$route.params.id}`, this.product);
        }
        this.$router.push('/');
      } catch (error) {
        console.error(error);
      }
    }
  }
}
</script>