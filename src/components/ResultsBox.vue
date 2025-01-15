<template>
  <div id="result" class="result">
    <div class="result__calories">
      Tu consumo debería ser:
      <div class="result__calories-value">{{ results.calories }}</div>
      <div class="result__calories-label">calorías por día.</div>
    </div>
    <div>
      <ul class="result__macro-list">
        <li
          v-for="macro in results.macros"
          :key="macro.name"
          class="result__macro-item">
          <div class="result__macro-title">{{ macro.name }}</div>
          <div class="result__macro-value">{{ macro.value }}</div>
          <div class="result__macro-subtitle">gramos al día.</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResultsBox",
  props: {
    results: {
      type: Object,
      required: true,
    }
  },
};
</script>

<style lang="sass">
.result
  margin: 5rem 0
  font-size: 1rem
  &__calories
    margin-bottom: 2rem
    &-value
      margin-top: 0.25rem
      font-size: 3.75rem
      line-height: 1
      font-weight: bold
    &-title
      font-size: 1.15rem
      font-weight: normal
  &__macro
    &-list
      display: grid
      grid-template-columns: 1fr 1fr 1fr
      padding: 0
      margin: 0
      list-style: none
    &-item
      margin-bottom: 1rem
    &-title
      text-transform: uppercase
      color: var(--primary-color-500)
      font-weight: bold
      font-size: 0.85rem
      @media (max-width: 480px)
        font-size: 0.75rem
    &-value
      margin-top: 0.25rem
      font-size: 2.75rem
      line-height: 1
      font-weight: bold
    &-subtitle
      font-size: 1rem
      font-weight: normal
</style>