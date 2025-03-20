<script>
import { activitiesList } from "../data/activitiesList";

export default {
  name: "ActivitiesComponent",
  data() {
    return {
      activitiesList
    }
  },
}
</script>

<template>
  <div class="activities">
    <div class="activities__container _container">
      <div class="activities__text">
        <h2 class="activities__title _title-2">Search through more than 11 million social media profiles</h2>
        <h5 class="activities__subtitle">Heepsy’s search filters help you find exactly what you’re looking for, and our influencer reports provide you with the metrics</h5>
      </div>
      <ul class="activities__list _flex _ai-c _jc-sb _gap-x-16">
        <li v-for="(item, index) in activitiesList" :key="index">
          <div class="_title-2">{{ item.number }}</div>
          <span>{{ item.name }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss">
.activities {
  padding: 120px 0;
  background-color: #231a36;
  &__title,
  &__list div {
    color: #fff;
  }
  &__subtitle,
  &__list span {
    color: #7b9292;
  }
  &__title {
    margin-bottom: 18px;
  }
  &__list {
    margin: 80px auto 0;
    padding: 0 157px;
    @media(max-width: 992px) {
      padding: 0 75px;
    }
    @media(max-width: 768px) {
      padding: 0;
    }
  }
  &__text {
    margin: 0 auto;
    text-align: center;
    padding: 0 215px;
    @media(max-width: 992px) {
      padding: 0 135px;
    }
    @media(max-width: 768px) {
      padding: 0 48px;
    }
  }
}
</style>
