<template>
  <div class="product-form">
    <h3>Add a New Product</h3>
    <form @submit.prevent="submitProduct">
      <div class="form-group">
        <label for="name">Product Name:</label>
        <input v-model="product.name" id="name" required />
      </div>

      <div class="form-group">
        <label for="price">Product Price:</label>
        <input v-model="product.price" id="price" type="number" required />
      </div>

      <div class="form-group">
        <label for="description">Product Description:</label>
        <textarea v-model="product.description" id="description" required></textarea>
      </div>

      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        name: '',
        price: null,
        description: ''
      }
    };
  },
  methods: {
    submitProduct() {
      this.$emit('add-product', { ...this.product });
      this.product = { name: '', price: null, description: '' };
    }
  }
};
</script>

<style scoped>
.product-form {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 5px;
  max-width: 400px;
  margin: 20px auto;
}

.form-group {
  margin-bottom: 10px;
}

input,
textarea {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

button {
  background-color: #42b983;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #358a66;
}
</style>
