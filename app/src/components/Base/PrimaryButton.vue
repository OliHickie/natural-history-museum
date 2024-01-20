<template>
  <button class="button">
    <slot />
  </button>
</template>

<style lang="scss" scoped>
.button {
  border: none;
  border-radius: 0.25rem;
  padding: 0.3rem 1rem;
  font-size: 1rem;
  line-height: 1.5;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  background-color: #014D4E;
  color: #fff;
  font-size: 0.8rem;
  &:hover {
    opacity: 0.8;
  }
}
</style>