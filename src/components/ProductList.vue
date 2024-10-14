<template>
  <div class="product-list">
    <h3>Product List</h3>
    <ul v-if="products.length">
      <li v-for="(product, index) in products" :key="index" class="product-item">
        <span v-if="editIndex !== index">
          {{ product.name }} - {{ product.price }} - {{ product.description }}
          <button @click="editProduct(index)">Edit</button>
        </span>
        <span v-else>
          <input v-model="editProductData.name" placeholder="Product Name" />
          <input v-model="editProductData.price" type="number" placeholder="Price" />
          <textarea v-model="editProductData.description" placeholder="Description"></textarea>
          <button @click="saveEdit(index)">Save</button>
        </span>
      </li>
    </ul>
    <p v-else>No products added yet.</p>
  </div>
</template>

<script>
export default {
  props: {
    products: Array
  },
  data() {
    return {
      editIndex: -1,
      editProductData: { name: '', price: '', description: '' }
    };
  },
  methods: {
    editProduct(index) {
      this.editIndex = index;
      this.editProductData = { ...this.products[index] };
    },
    saveEdit(index) {
      this.$emit('edit-product', { index, updatedProduct: this.editProductData });
      this.editIndex = -1;
    }
  }
};
</script>

<style scoped>
.product-list {
  margin: 20px auto;
  max-width: 600px;
  background-color: #2a2a2a;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  color: #f0f0f0;
}

h3 {
  color: #42b983;
  margin-bottom: 15px;
}

.product-item {
  margin-bottom: 15px;
  list-style-type: none;
  padding: 10px;
  background-color: #3c3c3c;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.product-item:hover {
  background-color: #444;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #358a66;
}

input,
textarea {
  padding: 10px;
  border-radius: 4px;
  border: 1px solid #666;
  margin-bottom: 10px;
  width: calc(100% - 20px);
  background-color: #444;
  color: #f0f0f0;
}

input::placeholder,
textarea::placeholder {
  color: #aaa;
}
</style>
