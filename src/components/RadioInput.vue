<template>
  <label :for="name" class="radio" @click="changeValue">
    <input
      type="radio"
      :name="name"
      :checked="modelValue == value"
      :value="value"
      @change="changeValue"
      class="radio__check"
    />
    <div class="radio__box" :class="{ 'has-check': hasCheckIcon }">
      <div class="radio__icon" v-if="hasCheckIcon"></div>
      <div class="radio__text">
        <slot></slot>
      </div>
    </div>
  </label>
</template>

<script>
export default {
  name: "RadioInput",
  props: {
    name: {
      type: String,
      default: "",
      required: true,
    },
    modelValue: {
      default: "",
    },
    value: {
      default: undefined,
    },
    hasCheckIcon: {
      type: Boolean,
      default: true,
    },
  },
  methods: {
    changeValue() {
      this.$emit("update:modelValue", this.value);
    },
  },
};
</script>

<style lang="sass">
.radio
  display: block
  margin: 0.25em 0
  &__check
    height: 1px
    overflow: hidden
    width: 1px
    position: absolute
    clip: rect(1px 1px 1px 1px)
    clip-path: inset(50%)
    white-space: nowrap
    &:checked
      & + .radio__box
        background-color: var(--primary-color-100)
        border-color: var(--primary-color-600)
      & + .radio__box .radio__icon
        border-color: var(--primary-color-500)
      & + .radio__box .radio__icon:after
        content: ""
        display: block
        height: 1rem
        width: 1rem
        position: absolute
        top: 50%
        left: 50%
        transform: translate(-50%, -50%)
        border-radius: 999px
        background-color: var(--primary-color-400)
  &__box
    padding: 1em
    background-color: var(--gray-50)
    border: 1px solid var(--primary-color-300)
    border-radius: 0.25rem
    cursor: pointer
    &.has-check
      display: grid
      grid-template-columns: 3rem 1fr
      align-items: center
  &__icon
    height: 2rem
    width: 2rem
    border-radius: 9999px
    border: 1px solid var(--primary-color-300)
    position: relative
  &__text p
    margin: 0 0 0.25rem 0
</style>