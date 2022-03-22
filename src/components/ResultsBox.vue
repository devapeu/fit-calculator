<template>
  <div id="result" class="fit__result">
    <div class="fit__result__left">
      Tu consumo debería ser:
      <div class="fit__text-xl">
        {{ results.calories }}
        <div class="fit__text-xl__subtitle">calorías por día.</div>
      </div>
    </div>
    <div class="fit__result__right">
      <ul class="fit__macro-list">
        <li
          v-for="macro in results.macros"
          :key="macro.name"
          class="fit__macro-list__item"
        >
          <div class="fit__macro-list__title">{{ macro.name }}</div>
          <div class="fit__text-lg">
            {{ macro.value }}
            <div class="fit__text-lg__subtitle">gramos al día.</div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResultsBox",
  props: ["results"],
};
</script>

<style lang="scss">
.fit__result {
  margin: 5rem 0;
  font-size: 1rem;
}

.fit__result__left {
  margin-bottom: 2rem;
}

.fit__macro-list {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  padding: 0;
  margin: 0;
  list-style: none;
}

.fit__macro-list__item {
  margin-bottom: 1rem;
}

.fit__macro-list__title {
  text-transform: uppercase;
  color: var(--primary-color-500);
  font-weight: bold;
  font-size: 0.85rem;
}

.fit__text-xl {
  font-size: 3.75rem;
  line-height: 1;
  font-weight: bold;

  .fit__text-xl__subtitle {
    font-size: 1.15rem;
    font-weight: normal;
  }
}

.fit__text-lg {
  font-size: 2.75rem;
  line-height: 1;
  font-weight: bold;

  .fit__text-lg__subtitle {
    font-size: 1rem;
    font-weight: normal;
  }
}
</style>