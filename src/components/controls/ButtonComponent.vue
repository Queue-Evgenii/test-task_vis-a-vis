<script>
export default {
  name: "ButtonComponent",
  methods: {
    emitClick(e) {
      this.$emit("clickHoisting", e)
    },
  },
}
</script>

<template>
  <button type="button" @click="emitClick">
    <slot></slot>
  </button>
</template>