<script>
import ButtonComponent from "./controls/ButtonComponent.vue";
import LogoComponent from "./shared/LogoComponent.vue";

import { homeMenu } from "../data/homeMenu"
import { resourcesMenu } from "../data/resourcesMenu"
import { communityMenu } from "../data/communityMenu"
import { mainLinksMenu } from "../data/mainLinksMenu"
import { socialsMenu } from "../data/socialsMenu"

export default {
  name: "FooterComponent",
  components: {
    ButtonComponent,
    LogoComponent,
  },
  props: {
    subscribtionEmail: {
      type: String,
      required: true,
    }
  },
  data() {
    return {
      homeMenu,
      resourcesMenu,
      communityMenu,
      mainLinksMenu,
      socialsMenu,
    }
  },
  methods: {
    getIconPath(name) {
      return new URL(`../assets/icons/${name}.svg`, import.meta.url).href;
    },
  },
}
</script>

<template>
  <footer class="footer">
    <div class="footer__top">
      <div class="footer__container _container _flex _ai_c _jc-sb _gap-x-96">
        <div class="footer__navigation _flex _ai-c _gap-x-48">
          <div class="footer__section">
            <h3 class="_title-3">{{ homeMenu.name }}</h3>
            <ul>
              <li v-for="(item, index) in homeMenu.data" :key="index">
                <a :href="item.url">{{ item.name }}</a>
              </li>
            </ul>
          </div>
          <div class="footer__section">
            <h3 class="_title-3">{{ resourcesMenu.name }}</h3>
            <ul>
              <li v-for="(item, index) in resourcesMenu.data" :key="index">
                <a :href="item.url">{{ item.name }}</a>
              </li>
            </ul>
          </div>
          <div class="footer__section">
            <h3 class="_title-3">{{ communityMenu.name }}</h3>
            <ul>
              <li v-for="(item, index) in communityMenu.data" :key="index">
                <a :href="item.url">{{ item.name }}</a>
              </li>
            </ul>
          </div>
          <div class="footer__section">
            <h3 class="_title-3">{{ mainLinksMenu.name }}</h3>
            <ul>
              <li v-for="(item, index) in mainLinksMenu.data" :key="index">
                <a :href="item.url">{{ item.name }}</a>
              </li>
            </ul>
          </div>
        </div>
        <div class="footer__section">
          <h3 class="_title-3">Subscribe Cirkle Newsletter</h3>
          <p>Subscribe to be the first one to know about updates. Enter your email</p>
          <div class="footer__input _flex _ai-c">
            <input
              type="text"
              placeholder="Email Address"
              name="search"
              id="search"
              :value="subscribtionEmail"
              @input="$emit('update:subscribtionEmail', $event.target.value)"
            >
            <ButtonComponent>Subscribe</ButtonComponent>
          </div>
        </div>
      </div>
    </div>
    <div class="footer__bottom">
      <div class="footer__container _container _flex _ai-c _jc-sb _gap-x-48">
        <div>Besnik Creative Agency.</div>
        <LogoComponent type="light" />
        <ul class="footer__socials _flex _ai-c _gap-x-8">
          <li v-for="(item, index) in socialsMenu" :key="index">
            <a :href="item.url">
              <img :src="getIconPath(item.name)" alt="">
            </a>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<style lang="scss">
.footer {
  &__top {
    padding: 78px 0 85px;
    background-color: #2b2b39;
    color: #fff;
  }
  &__bottom {
    padding: 31px 0;
    background-color: #20202d;
    color: #fff;
  }
  &__navigation {
    flex: 1 0 auto;
  }
  &__section,
  &__section ul {
    display: flex;
    flex-direction: column;
    row-gap: 24px;
    li:hover {
      text-decoration: underline;
    }
  }
  &__input {
    border: 1px solid #fff;
    border-radius: 12px;
    overflow: hidden;
    input {
      padding: 18px 24px;
      flex: 1 1 auto;
      min-width: 0;
    }
    button {
      flex: 0 0 126px;
      height: 100%;
      border-radius: 12px 0 0 12px;
      background-color: #fff;
      color: #2b2b39;
      font-weight: 500;
    }
  }
  &__socials li {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2px;
    background-color: #fff;
    border-radius: 50%;
  }
}
</style>