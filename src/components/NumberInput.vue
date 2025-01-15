<template>
  <label :for="name" class="input">
    <input
      type="number"
      :value="modelValue"
      :name="name"
      @input="$emit('update:modelValue', $event.target.value)"
      class="input__field"
      min="0"
    />
    <span class="input__suffix">{{ suffix }}</span>
  </label>
</template>

<script>
export default {
  name: "TextInput",
  props: {
    modelValue: { default: "" },
    name: String,
    suffix: String,
  },
  emits: ["update:modelValue"],
};
</script>

<style lang="sass">
.input
  position: relative
  &__field
    width: 100%
    font-size: 1.25rem
    padding: 1em
    border: 1px solid var(--primary-color-300)
    border-radius: 0.25rem
    &::-webkit-outer-spin-button,
    &::-webkit-inner-spin-button
      -webkit-appearance: none
      margin: 0
    &[type="number"]
      -moz-appearance: textfield
  &__suffix
    position: absolute
    top: 0
    bottom: 0
    right: 1em
</style>