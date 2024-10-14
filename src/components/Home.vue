<template>
  <div class="home-container">
    <p class="name">Nice Dimple Sagarino</p>
    <p class="program">Program: BSIT-3</p>
    <nav class="navigation">
      <router-link to="/" class="nav-link">Home</router-link>
      <router-link to="/products" class="nav-link">Products</router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Home'
};
</script>

<style scoped>
.home-container {
  background-color: #333;
  color: #f0f0f0;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.name {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.program {
  font-size: 18px;
  margin-bottom: 20px;
}

.navigation {
  display: flex;
  gap: 15px;
}

.nav-link {
  color: #ffffff;
  text-decoration: none;
  padding: 10px 15px;
  background-color: #444;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.nav-link:hover {
  background-color: #555;
}
</style>
