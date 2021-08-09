<template>
  <div class="v-modal">
    <v-input
      label="Наименование товара"
      inputLabel="Введите наименование товара"
      v-model="name"
    />
    <v-textarea
      label="Описание товара"
      textareaLabel="Введите описание товара"
      v-model="description"
    />
    <v-input
      label="Ссылка на изображение товара"
      inputLabel="Введите введите ссылку"
      v-model="photo"
    />
    <v-input label="Цена товара" inputLabel="Введите цену" v-model="price" />
    <v-button @click.native="createProduct" :disabled="isSubmitDisabled"
      >Добавить</v-button
    >
  </div>
</template>

<script>
import VInput from '@/components/VInput.vue';
import VButton from '@/components/VButton.vue';
import VTextarea from '@/components/VTextarea.vue';

export default {
  name: 'VFilterBox',
  components: {
    VInput,
    VButton,
    VTextarea,
  },
  data() {
    return {
      name: '',
      description: '',
      photo: '',
      price: '',
    };
  },
  computed: {
    isSubmitDisabled() {
      return (
        this.name === '' ||
        this.description === '' ||
        this.photo === '' ||
        this.price === ''
      );
    },
  },
  methods: {
    createProduct() {
      this.$emit('on-product-create', {
        name: this.name,
        description: this.description,
        photo: this.photo,
        price: this.price,
      });
      this.reset();
    },

    reset() {
      this.name = '';
      this.description = '';
      this.photo = '';
      this.price = '';
    },
  },
};
</script>

<style lang="scss">
.v-modal {
  position: relative;
  min-width: 332px;
  padding: 24px;
  border-radius: 4px;
  background: #fffefb;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
}
</style>
