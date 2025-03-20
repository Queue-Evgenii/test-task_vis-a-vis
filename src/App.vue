<script>
import "./assets/reset.css";
import "./assets/style.scss"
import AchievmentsComponent from "./components/AchievmentsComponent.vue";

import ActivitiesComponent from "./components/ActivitiesComponent.vue";
import PreviewComponent from "./components/PreviewComponent.vue";
import LayoutDefault from "./layouts/LayoutDefault.vue";

export default {
  name: "App",
  components: {
    LayoutDefault,
    PreviewComponent,
    ActivitiesComponent,
    AchievmentsComponent,
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
   <AchievmentsComponent />
  </LayoutDefault>
</template>

<style lang="scss">
</style>
