<script>
import FooterComponent from "../components/FooterComponent.vue";
import HeaderComponent from "../components/HeaderComponent.vue";

import { headerMenu } from "../data/headerMenu";

export default {
  name: "LayoutDefault",
  components: {
    HeaderComponent,
    FooterComponent,
  },
  data() {
    return {
      headerMenu,
      searchValue: "",
      subscribtionEmail = "",
    }
  }
}
</script>

<template>
  <HeaderComponent
    :headerMenu="headerMenu"
    :searchValue="searchValue"
    @update:searchValue="value => searchValue = value"
  />
  <slot></slot> {{ searchValue }}
  <FooterComponent
    :subscribtionEmail="subscribtionEmail"
    @update:subscribtionEmail="value => subscribtionEmail = value"
  />
</template>

<style lang="scss"></style>
