<template>
  <nav>
    <div class="content">
      <EarthIcon class="content__earth-icon" />
      <h1>
        Natural History Museum
      </h1>
    </div>
    <div class="menu">
      <NavIcon class="menu__icon" />
    </div>
  </nav>
</template>

<script>
import EarthIcon from './icons/EarthIcon.vue';
import NavIcon from './icons/NavIcon.vue';

export default {
  name: 'TopNav',
  components: {
    EarthIcon,
    NavIcon
  },
}

</script>

<style lang="scss">
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #C0C0C0;
    padding: 8px 24px;
    .content {
      display: flex;
      align-items: center;
      &__earth-icon {
        margin-right: 1.5rem;
        width: 50px;
        height: 50px;
      }
    }
    .menu {
      &__icon {
        width: 30px;
        height: 30px;
      }
    }
  }
</style>
