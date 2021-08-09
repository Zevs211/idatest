<template>
  <div class="input">
    <div class="input__label">
      {{ label }}
      <div class="dot"></div>
    </div>
    <div class="input__container">
      <input :placeholder="inputLabel" :value="value" @input="onInput" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'VInput',
  props: {
    label: {
      type: String,
    },
    inputLabel: {
      type: String,
    },
    value: {
      type: String,
    },
  },
  methods: {
    onInput(event) {
      this.$emit('input', event.target.value);
    },
  },
};
</script>

<style lang="scss">
.input {
  width: 100%;
  margin-bottom: 16px;
  &__label {
    display: flex;
    width: 100%;
    height: 13px;
    user-select: none;
    margin-bottom: 4px;

    // font-family: Source Sans Pro;
    font-family: 'Source Sans Pro', sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 10px;
    line-height: 13px;

    letter-spacing: -0.02em;

    color: #49485e;
    .dot {
      width: 4px;
      height: 4px;

      background: #ff8484;
      border-radius: 4px;
    }
  }
  &__container {
    position: relative;
    display: flex;
    align-items: center;
    padding-top: 10px;
    padding-bottom: 10px;
    padding-left: 16px;
    padding-right: 16px;
    height: 36px;
    background-color: #fffefb;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    input {
      width: 100%;
      outline: none;
      font-size: 12px;
    }
    input::-webkit-input-placeholder {
      font-family: 'Source Sans Pro', sans-serif;
    }

    input:-ms-input-placeholder {
      font-family: 'Source Sans Pro', sans-serif;
    }

    input:-moz-placeholder {
      font-family: 'Source Sans Pro', sans-serif;
    }

    input::-moz-placeholder {
      font-family: 'Source Sans Pro', sans-serif;
    }
  }
}
</style>
