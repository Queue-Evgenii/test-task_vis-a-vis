<script>
import "./assets/reset.css";
import "./assets/style.scss"

import ActivitiesComponent from "./components/ActivitiesComponent.vue";
import PreviewComponent from "./components/PreviewComponent.vue";
import LayoutDefault from "./layouts/LayoutDefault.vue";

export default {
  name: "App",
  components: {
    LayoutDefault,
    PreviewComponent,
    ActivitiesComponent,
  },
  data() {
    return {

    }
  },
}
</script>

<template>
  <LayoutDefault>
   <PreviewComponent />
   <ActivitiesComponent />
  </LayoutDefault>
</template>

<style lang="scss">
</style>
