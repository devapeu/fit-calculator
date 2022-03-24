<template>
  <section class="fit__promo">
    <slot></slot>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
.fit__promo {
  margin: 10rem auto 5rem;
  max-width: 64rem;
  padding: 5rem;
  background: white;
  text-align: center;

  @media screen and (max-width: 480px) {
    padding: 3rem;
  }

  .title {
    font-size: 2rem;
    line-height: 1;

    @media screen and (max-width: 480px) {
      font-size: 1.5rem; 
    }
  }

  .btn {
    margin: 2rem 0 0;
    font-size: 1rem;
    background-color: var(--gray-50);
    border: 2px solid var(--primary-color-500);
    color: var(--primary-color-500);
  }
}
</style>