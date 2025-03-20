<script>
import ButtonComponent from './controls/ButtonComponent.vue';

export default {
  name: "PreviewComponent",
  components: {
    ButtonComponent,
  },
  methods: {
    emitAboutBtnClick() {
      this.$emit("aboutBtnClickHoisting");
    },
    emitInviteBtnClick() {
      this.$emit("inviteBtnClickHoisting");
    },
  },
}
</script>

<template>
  <div class="preview">
    <div class="preview__container _container _flex _ai-c _jc-sb _gap-x-32">
      <div class="preview__section content-preview">
        <span class="content-preview__marker">Netbook community</span>
        <h1 class="content-preview__title _title-1">Your Solutions For Community!</h1>
        <h4 class="content-preview__subtitle">More than 2 billion people in over countries use socibook to stay in touch with friends & family.</h4>
        <div class="content-preview__actions _flex _ai-c _gap-x-16">
          <ButtonComponent class="_button-1">About More</ButtonComponent>
          <ButtonComponent class="_button-2">Invite Friend</ButtonComponent>
        </div>
      </div>
      <div class="preview__section _image">
        <img src="../assets/preview.png" alt="">
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.preview {
  background: linear-gradient(270.76deg, #D4E7FE -15.24%, #FFFFFF 78.85%);
  padding: 72px 0;
  &__section {
    flex: 0 1 45%;
  }
}
.content-preview {
  &__marker {
    display: inline-block;
    color: #217bf4;
    background-color: #e7f1fe;
    border-radius: 8px;
    padding: 12px 30px;
  }
  &__marker,
  &__title {
    margin-bottom: 20px;
  }
  &__subtitle {
    margin-bottom: 40px;
    line-height: 1.5;
  }
}
</style>
