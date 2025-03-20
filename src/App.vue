<script>
import "./assets/reset.css";
import "./assets/style.scss"
import PreviewComponent from "./components/PreviewComponent.vue";
import LayoutDefault from "./layouts/LayoutDefault.vue";

export default {
  name: "App",
  components: {
    LayoutDefault,
    PreviewComponent,
  },
}
</script>

<template>
  <LayoutDefault>
   <PreviewComponent />
  </LayoutDefault>
</template>

<style lang="scss">
</style>
