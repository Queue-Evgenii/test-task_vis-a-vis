<script>
export default {
  name: "LogoComponent",
  props: {
    type: {
      type: String,
      default: "dark",
      validator: (value) => ["dark", "light"].includes(value),
    },
  }
}
</script>

<template>
  <div class="_image">
    <img v-if="type === 'dark'" src="../../assets/logo-dark.png" alt="">
    <img v-else src="../../assets/logo-light.png" alt="">
  </div>
</template>
