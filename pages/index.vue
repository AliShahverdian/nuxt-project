<template>
  <div class="card-container">
    <div v-for="el in products" :key="el" class="card">
      <div>{{ el.title }}</div>
      <div>{{ el.brand }}</div>
      <div>{{ el.price }}</div>
      <div>{{ el.id }}</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      products: [],
    }
  },
  async created() {
    this.products = await this.$axios.$get('http://localhost:3000/products')
    console.log('=================', this.products)
  },
}
</script>
<style>
.card {
  border: solid 2px black;
  width: 300px;
  margin: 16px;
  font-size: 24px;
  text-align: center;
}
.card-container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
