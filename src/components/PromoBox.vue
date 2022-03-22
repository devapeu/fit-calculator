<template>
  <section class="fit__promo">
    <slot></slot>
  </section>
</template>

<script>
export default {

}
</script>

<style lang="scss">
.fit__promo {
  margin: 10rem 0 5rem;
  padding: 5rem 0;
  background: white;
  text-align: center;

  .title {
    font-size: 2rem;
    line-height: 1;
  }

  .btn {
    margin: 2rem 0;
    font-size: 1rem;
    background-color: var(--gray-50);
    border: 2px solid var(--primary-color-500);
    color: var(--primary-color-500);
  }

}
</style>