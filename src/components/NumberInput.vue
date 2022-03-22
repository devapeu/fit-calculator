<template>
  <label :for="name" class="fit__input fit__input--number">
    <input
      type="number"
      :value="modelValue"
      :name="name"
      @input="$emit('update:modelValue', $event.target.value)"
      class="fit__input__field"
    />
    <span class="fit__input__suffix">{{ suffix }}</span>
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

<style>
.fit__input {
  position: relative;
}

.fit__input__field {
  width: 100%;
  font-size: 1.25rem;
  padding: 1em;
  border: 1px solid var(--primary-color-300);
  border-radius: 0.25rem;
}

.fit__input__suffix {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 1em;
}
</style>