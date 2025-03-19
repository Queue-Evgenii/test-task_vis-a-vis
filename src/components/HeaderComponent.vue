<script>
import ButtonComponent from "./shared/ButtonComponent.vue";

export default {
  name: "HeaderComponent",
  components: {
    ButtonComponent,
  },
  props: {
    headerMenu: {
      type: Array,
      default: [],
    },
  },
  data() {
    return {
      isSearchFocused: false,
    }
  },
  methods: {
    emitClick() {
      this.$emit("loginClickHoisting");
    },
  },
}
</script>

<template>
  <header class="header">
    <div class="header__container _container _flex _ai-c _jc-sb _gap-x-48">
      <div class="header__logo _image">
        <img src="../assets/logo.png" alt="">
      </div>
      <ul class="header__menu _flex _ai-c _gap-x-32">
        <li v-for="(item, index) in headerMenu" :key="index">
          <a :href="item.url">
            {{ item.name }}
          </a>
        </li>
      </ul>
      <div class="header__search search-header _flex _ai-c">
        <div :class="['search-header__wrapper _flex _ai-c _gap-x-8', isSearchFocused ? '_active' : '',]">
          <span>
            <img src="../assets/search-icon.svg" alt="">
          </span>
          <input
            type="text"
            name="search"
            id="search"
            placeholder="Search Here..."
            @focus="isSearchFocused = true"
            @blur="isSearchFocused = false"
            :class="[
              'search-header__input',
              
            ]"
          >
        </div>
      </div>
      <ButtonComponent @clickHoisting="emitClick" class="header__button _button-1">
        Log in
      </ButtonComponent>
    </div>
  </header>
</template>

<style lang="scss">
.header {
  padding: 26px 0;
  border-bottom: 1px solid #e2edfe;
}
.header__logo {
  max-width: 143px;
}
.header__menu {
  li {
    font-weight: 600;
    &:hover {
      text-decoration: underline;
    }
  }
}
.header__search {
  flex: 1 1 auto;
}
.search-header {
  justify-content: right;
  &__wrapper {
    transition: max-width 0.3s ease;
    flex: 1 1 100%;
    max-width: 126px;
    &._active {
      max-width: 100%;
      border-bottom: 1px solid #e5e5e5;
    }
    span {
      display: inline-flex;
    }
  }
  &__input {
    flex: 1 1 100%;
    width: 100%;
    padding: 12px 0;
  }
}
.header__button,
.header__logo {
  flex-shrink: 0;
}
</style>
