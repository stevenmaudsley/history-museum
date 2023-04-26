<template>
  <div
    class="header d-flex flex-row w-100 align-items-center justify-content-between"
  >
    <section class="d-flex flex-row align-items-center pl-2">
      <!-- Would reuse icon component here -->
      <img class="header__image mr-2" src="@/assets/globe.png" />
      <h2 class="px-4">Natural History Museum</h2>
    </section>
    <!-- Would reuse icon component here -->
    <img class="header__image" src="@/assets/menu.png" />
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>
<style lang="scss" scoped>
.header {
  background-color: #e5e4e2;

  &__image {
    max-height: 3rem;
    aspect-ratio: 1/1;
  }
}
</style>
