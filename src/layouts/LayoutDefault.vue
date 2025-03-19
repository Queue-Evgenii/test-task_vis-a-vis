<script>
import FooterComponent from '../components/FooterComponent.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import { headerMenu } from '../data/headerMenu';

export default {
  name: "LayoutDefault",
  components: {
    HeaderComponent,
    FooterComponent,
  },
  data() {
    return {
      headerMenu,
    }
  }
}
</script>

<template>
  <HeaderComponent :headerMenu="headerMenu" />
  <slot></slot>
  <FooterComponent />
</template>

<style lang="scss"></style>
