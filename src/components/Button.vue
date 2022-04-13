<template>
  <button>
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    variant: {
      type: String,
      required: false,
      default: "contained",
    },
  },
};
</script>

<style lang="css" scoped>
button {
  padding: 8px 6px;
  background: transparent;
}
</style>