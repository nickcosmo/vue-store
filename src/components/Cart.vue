<template>
  <div class="cartContainer">
    <h1 v-if="checkCartZero">Cart is Empty!</h1>
    <cart-item class="item" v-for="article in articles"
      :key="article.id"
      :id="article.id"
      :count="article.count"
      :title="article.title"
      :price="article.price"
      :desc="article.description"
      :image="article.image"
    ></cart-item>
    <div class="divider"></div>
    <h2>Total Price: {{ $store.getters.totalPrice }}</h2>
  </div>
</template>

<script>
import CartItem from './CartItem.vue';

export default {
  data() {
    return {
      articles: this.$store.state.articles,
    }
  },
  computed: {
    checkCartZero() {
        return this.$store.getters.totalCount === 0;
    }
  },
  components: {
    CartItem,
  }
}
</script>

<style scoped>
  .cartContainer {
    text-align: center;
    align-items: center;
  }

  .item {
    margin: 10px auto 0px auto;
  }

  h1 {
    margin-top: 40px;
  }

  .divider {
    margin: 10px auto;
    width: 50%;
    max-width: 500px;
    height: 5px;
    background-color: black;
  }
</style>