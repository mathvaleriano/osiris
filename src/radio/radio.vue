<template>
  <label
    :class="[
      'o-radio',
      `o-radio--${size}`, {
        'is-disabled': disabled,
        'is-checked': isChecked
    }]"
    role="radio"
  >
    <input
      :name="name"
      :value="value"
      v-model="modelValue"
      :disabled="disabled"
      type="radio"
      class="o-radio__inner"
      aria-hidden="true"
      @change.prevent.stop="handleChange"
    >
    <span class="o-radio__label">
      <slot>
        {{ label }}
      </slot>
    </span>
  </label>
</template>

<script>
export default {
  name: 'ORadio',
  model: {
    prop: 'modelValue',
    event: 'change',
  },
  props: {
    label: [String, Number],
    disabled: Boolean,
    modelValue: {
      type: [String, Number, Boolean],
      default: undefined,
    },
    name: String,
    value: [Number, String, Boolean],
    size: {
      type: String,
      default: 'medium',
    },
  },
  computed: {
    isChecked() {
      return this.modelValue === this.value;
    },
  },
  methods: {
    handleChange() {
      this.$emit('change', this.value);
    },
  },
};
</script>
