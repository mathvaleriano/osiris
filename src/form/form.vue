<template>
  <form
    :class="[`o-form--${labelPosition}`]"
    :style="{ width }"
    class="o-form"
    @submit="handleSubmit">
    <slot />
  </form>
</template>

<script>
export default {

  name: 'OFormItem',

  props: {
    labelPosition: {
      type: String,
      default: 'top',
    },

    width: {
      type: String,
      default: '100%',
    },

    labelWidth: {
      type: String,
      default: '100px',
    },
  },

  provide() {
    return {
      labelWidth: this.labelWidth,
    };
  },

  methods: {
    handleSubmit() {
      return this.$emit('submit');
    },
  },
};
</script>
