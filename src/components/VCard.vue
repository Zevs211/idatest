<template>
  <div
    class="card"
    @mouseover="isCardOnFocus = true"
    @mouseleave="isCardOnFocus = false"
  >
    <img class="card__img" :src="product.photo" alt="" />
    <div>
      <div class="card__name">{{ product.name }}</div>
      <div class="card__description">{{ product.description }}</div>
      <div class="card__price">{{ product.price }}</div>
    </div>
    <transition name="fade">
      <div v-if="isCardOnFocus" class="card__trash" @click="remove">
        <img src="@/assets/img/icon-delete.svg" />
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'VCard',
  props: {
    product: {
      type: Object,
      default: () => ({
        id: 0,
        photo: '',
        description: '',
        price: '',
      }),
    },
  },
  data() {
    return {
      isCardOnFocus: false,
    };
  },
  methods: {
    remove() {
      this.$emit('remove', this.product.id);
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  max-width: 440px;
  min-height: 364px;
  max-height: 424px;

  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  position: relative;
  cursor: pointer;
  &__img {
    height: 200px;
    width: 100%;
    object-fit: cover;
  }
  &__name {
    margin-left: 16px;
    margin-top: 16px;
    font-family: 'Source Sans Pro', sans-serif;
    font-style: normal;
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;

    color: #3f3f3f;
  }
  &__description {
    margin-left: 16px;
    margin-top: 16px;
    font-family: 'Source Sans Pro', sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 20px;

    color: #3f3f3f;
  }
  &__price {
    margin-left: 16px;
    margin-top: 16px;
    margin-bottom: 24px;
    font-family: 'Source Sans Pro', sans-serif;
    font-style: normal;
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;

    color: #3f3f3f;
  }
  &__trash {
    position: absolute;
    padding-top: 8px;
    padding-left: 8px;
    top: -8px;
    right: -8px;
    width: 32px;
    height: 32px;
    background: #ff8484;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    cursor: pointer;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
</style>
