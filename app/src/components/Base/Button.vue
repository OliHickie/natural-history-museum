<template>
  <button :class="['button', type]">
    <slot />
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    type: {
      type: String,
      default: 'primary',
    },
  },
}

</script>

<style lang="scss" scoped>
.button {
  border: none;
  border-radius: 0.5rem;
  padding: 0.3rem 1rem;
  font-size: 1rem;
  line-height: 1.5;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  
  font-size: 0.8rem;
  &.primary {
    background-color: #014D4E;
    border: 1px solid #014D4E;
    color: #fff;
  }
  &.secondary {
    background-color: #fff;
    color: #014D4E;
    border: 1px solid #014D4E;
  }
  &:hover {
    opacity: 0.6;
  }
}
</style>