<template>
  <teleport to="body">
    <div class="fit__modal">
      <div class="fit__modal__content">
        <a
          class="btn btn--orange fit__btn"
          href="https://ricardoeliascoach.com/nutricion"
          >Planes de Nutrición para Mujeres</a
        >
        <a class="btn fit__btn" href="https://liaolite.com/nutricion"
          >Planes de Nutrición para Hombres</a
        >
      </div>
      <div class="fit__modal__background" @click="$emit('closeModal')"></div>
    </div>
  </teleport>
</template>

<script>
export default {};
</script>

<style lang="scss">
.fit__modal__content {
  background: white;
  padding: 3rem;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 10;
}
.fit__modal {
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.5);

  .btn {
    width: 100%;
    display: block;
    margin: 2rem 0 0;
    font-size: 1rem;
    background-color: var(--gray-50);
    border: 2px solid var(--primary-color-500);
    color: var(--primary-color-500);

    &.btn--orange {
      margin-top: 0;
      border: 2px solid #ea580c;
      color: #ea580c;
    }
  }
}

.fit__modal__background {
  height: 100%;
  width: 100%;
}
</style>