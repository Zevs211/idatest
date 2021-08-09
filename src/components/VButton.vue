<template>
  <button class="btn" :class="type">
    <slot />
  </button>
</template>

<script>
export default {
  name: 'VButton',
  props: {
    type: {
      type: String,
      default: 'filled',
    },
  },
};
</script>

<style lang="scss" scoped>
.btn {
  width: 100%;
  height: 36px;
  background: #7bae73;
  border-radius: 10px;

  font-family: Inter;
  font-style: normal;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;

  color: #ffffff;

  user-select: none;
  cursor: pointer;
  transition: color 0.25s, background-color 0.25s;
  &:disabled {
    background: #eeeeee;

    font-family: Inter;
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    text-align: center;
    letter-spacing: -0.02em;
    color: #b4b4b4;
  }
}
</style>
