<script>
import ButtonComponent from "./controls/ButtonComponent.vue";

export default {
  name: "AchievmentsComponent",
  components: {
    ButtonComponent,
  },
}
</script>

<template>
  <div class="achievments">
    <div class="achievments__container _container _flex _ai-c">
      <div class="achievments__cards _flex _ai-c _gap-x-24">
        <div class="achievments__card card-achievments">
          <div class="card-achievments__title _flex _ai-c _gap-x-8">
            <img src="../assets/icons/star.svg" alt="">
            <h4>4.8 Rating</h4>
          </div>
          <div class="card-achievments__subtitle _flex _ai-c _gap-x-8">
            <img src="../assets/people.png" alt="">
            <div><span>+836k</span> Members</div>
          </div>
          <p>More than 2 billion we people over countries use socibooks we to stay in touch with friends.</p>
          <a href="#" class="card-achievments__link _flex _ai-c _gap-x-8">
            Join Our Community
            <span></span>
          </a>
        </div>
        <div class="achievments__card card-achievments">
          <div class="card-achievments__title _flex _ai-c _gap-x-8">
            <img src="../assets/icons/trophy.svg" alt="">
            <h4>Awwwards</h4>
          </div>
          <div class="card-achievments__subtitle _flex _ai-c _gap-x-8">
            <img src="../assets/github.png" alt="">
            <div>
              Best of <span>2021</span> on Github
            </div>
          </div>
          <p>More than 2 billion we people over countries use socibooks we to stay in touch with friends.</p>
          <a href="#" class="card-achievments__link _flex _ai-c _gap-x-8">
            Go To Awards
            <span></span>
          </a>
        </div>
      </div>
      <div class="achievments__content">
        <span>Our Achievement</span>
        <h3 class="_title-2">We are Connecting You The Digital Life.</h3>
        <p>The scope the Social Media becomes crucial Is helps the business to directly engage with their needs and wants.</p>
        <ButtonComponent class="_button-1 _flex _ai-c _gap-x-8">
          Discover me
          <img src="../assets/icons/arrow-white.svg" alt="">
        </ButtonComponent>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.achievments {
  padding: 115px 0;
  background-color: #fbfbfb;
  color: #8c8c8c;
  &__container {
    column-gap: 90px;
    @media(max-width: 1200px) {
      column-gap: 40px
    }
  }
  &__card {
    display: flex;
    flex-direction: column;
    row-gap: 40px;
  }
  &__content {
    span {
      color: #217bf4;
    }
    h3 {
      color: #0a093d;
      margin-top: 12px;
      margin-bottom: 18px;
    }
    button {
      margin-top: 38px;
    }
  }
}

.card-achievments {
  padding: 42px 44px;
  border: 1px solid #e2edfe;
  border-radius: 14px;
  background-color: transparent; 
  transition: color, background-color, border .3s ease;
  &__title {
    color: #0a093d;
  }
  &__subtitle {
    font-weight: 600;
    img {
      height: 24px;
    }
    span {
      color: #217bf4;
    }
  }
  &__link {
    color: #4a4a56;
    span {
      display: inline-block;
      width: 10px;
      height: 10px;
      background: url("../assets/icons/arrow-grey.svg");
    }
  }
  &:hover {
    border-color: transparent;
    background-color: #fff;
    .card-achievments__link {
      color: #217bf4;
      span {
        background: url("../assets/icons/arrow-blue.svg");
      }
    }
  }
  @media(max-width: 1200px) {
    padding: 24px 28px;
  }
}
</style>