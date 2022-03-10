<template>
  <label :for="name" class="fit__radio" @click="changeValue">
    <input
      type="radio"
      :name="name"
      :checked="modelValue == value"
      :value="value"
      @change="changeValue"
      class="fit__radio__check"
    />
    <div class="fit__radio__box" :class="{ 'has-check': hasCheckIcon }">
      <div class="fit__radio__icon" v-if="hasCheckIcon"></div>
      <div class="fit__radio__text">
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

<style lang="scss">
.fit__radio {
  display: block;
  margin: 0.25em 0;
}

.fit__radio__check {
  height: 1px;
  overflow: hidden;
  width: 1px;
  position: absolute;
  clip: rect(1px 1px 1px 1px);
  clip-path: inset(50%);
  white-space: nowrap;
}

.fit__radio__box {
  padding: 1em;
  background-color: #fff;
  border: 1px solid #93c5fd;
  border-radius: 0.25rem;
  cursor: pointer;

  &.has-check {
    display: grid;
    grid-template-columns: 3rem 1fr;
    align-items: center;
  }
}

.fit__radio__check:checked {
  & + .fit__radio__box {
    background-color: #dbeafe;
    border-color: #2563eb;
  }

  & + .fit__radio__box .fit__radio__icon {
    border-color: #2563eb;
  }

  & + .fit__radio__box .fit__radio__icon:after {
    content: "";
    display: block;
    height: 1rem;
    width: 1rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 999px;
    background-color: #60a5fa;
  }
}

.fit__radio__icon {
  height: 2rem;
  width: 2rem;
  border-radius: 9999px;
  border: 1px solid #93c5fd;
  position: relative;
}

.fit__radio__text p {
  margin: 0 0 0.25rem 0;
}
</style>