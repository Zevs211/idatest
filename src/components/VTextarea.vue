<template>
  <div class="textarea">
    <div class="textarea__label">
      {{ label }}
    </div>
    <textarea
      rows="5"
      :placeholder="textareaLabel"
      :value="value"
      @input="onInput"
    />
  </div>
</template>

<script>
export default {
  name: 'VTextarea',
  props: {
    label: {
      type: String,
    },
    textareaLabel: {
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

<style lang="scss" scoped>
.textarea {
  width: 100%;
  margin-bottom: 16px;

  &__label {
    display: flex;
    width: 100%;
    height: 13px;
    user-select: none;
    margin-bottom: 4px;

    font-family: Source Sans Pro;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 20px;

    color: #3f3f3f;
  }
  textarea {
    padding: 10px 16px;
    width: 100%;
    background-color: #fffefb;
    border-radius: 4px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);

    overflow: auto;
    outline: none;

    box-sizing: border-box;
    resize: none;
    font-size: 12px;
  }
  textarea::-webkit-input-placeholder {
    font-family: 'Source Sans Pro', sans-serif;
  }

  textarea:-ms-input-placeholder {
    font-family: 'Source Sans Pro', sans-serif;
  }

  textarea:-moz-placeholder {
    font-family: 'Source Sans Pro', sans-serif;
  }

  textarea::-moz-placeholder {
    font-family: 'Source Sans Pro', sans-serif;
  }
}
</style>
