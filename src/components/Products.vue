<template>
  <div>
    <product-item v-for="article in articles"
      :key="article.id"
      :id="article.id"
      :image="article.image"
      :count="article.count"
      :title="article.title"
      :price="article.price"
      :desc="article.description"
    ></product-item>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue';

export default {
  data() {
    return {
      articles: this.$store.state.articles,
    }
  },
  components: {
    ProductItem
  }
}
</script>

<style scoped>
h2 {
  text-align: center;
}
div {
  margin: 2rem auto;
  max-width: 75rem;
  padding: 0;
  display: flex;
  justify-content: space-between;
}
</style>