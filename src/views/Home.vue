<template>
  <div class="home">
    <create-product @on-product-create="onProductCreated" />
    <div class="grid">
      <v-card
        v-for="product in products"
        :key="product.id"
        :product="product"
        @remove="removeProduct"
      />
    </div>
  </div>
</template>

<script>
import CreateProduct from '@/components/CreateProduct.vue';
import VCard from '@/components/VCard.vue';

export default {
  name: 'Home',
  components: {
    CreateProduct,
    VCard,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    onProductCreated(product) {
      product.id = this.products.length;
      this.products.push(product);
    },
    removeProduct(id) {
      const indexFound = this.products.indexOf((product) => product.id === id);
      this.products.splice(indexFound - 1, 1);
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: flex-start;
  &__heading {
    margin-top: 32px;
    margin-left: 32px;
    font-family: Source Sans Pro;
    font-style: normal;
    font-weight: 600;
    font-size: 28px;
    line-height: 35px;

    color: #3f3f3f;
  }
}
.grid {
  flex-grow: 1;
  width: 100%;
  padding-right: 16px;
  padding-top: 16px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  grid-gap: 1rem;
  margin-left: 16px;
}
</style>
