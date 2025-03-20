<script>
import ButtonComponent from './controls/ButtonComponent.vue';
import CheckboxComponent from './controls/CheckboxComponent.vue';
import InputComponent from './controls/InputComponent.vue';

export default {
  name: "OrderFormComponent",
  components: {
    InputComponent,
    CheckboxComponent,
    ButtonComponent,
  },
  data() {
    return {
      orderData: {
        first_name: "",
        last_name: "",
        sum: "",
        itn: "",
        isAgreed: false,
      }
    }
  }
}
</script>

<template>
  <div class="order">
    <div class="order__container _container">
      <h2 class="_title-2">Замовити послугу</h2>
      <form class="order__form form-order _flex _fd-col _gap-y-32">
        <InputComponent
          name="Ім’я"
          placeholder="Введіть ім’я"
          :value="orderData.first_name"
          @update:value="value => orderData.first_name = value"
        />
        <InputComponent
          name="Прізвище"
          placeholder="Введіть прізвище"
          :value="orderData.last_name"
          @update:value="value => orderData.last_name = value"
        />
        <InputComponent
          name="Сума угоди"
          placeholder="Введіть суму угоди"
          :value="orderData.sum"
          @update:value="value => orderData.sum = value"
        />
        <InputComponent
          name="Іпн"
          placeholder="Введіть іпн"
          :value="orderData.itn"
          @update:value="value => orderData.itn = value"
        />
        <CheckboxComponent
          name="Погоджуюсь з правилами та умовами"
          :value="orderData.isAgreed"
          @update:value="value => orderData.isAgreed = value"
        />
        <ButtonComponent class="_button-1">Відправити</ButtonComponent>
      </form>
    </div>
  </div>
</template>

<style lang="scss">
.order {
  font-family: "Noto Sans", sans-serif;
  padding: 95px 0;
  &__container {
    padding: 0 20px;
    max-width: 600px;
    h2 {
      color: #000;
      text-align: center;
      margin-bottom: 70px;
    }
  }
}

.form-order {
  .input-component,
  .checkbox-component {
    display: flex;
    flex-direction: column;
    row-gap: 8px;
    &__errors {
      display: flex;
      flex-direction: column;
      row-gap: 4px;
    }
    &__error {
      color: #eb5757;
    }
    label {
      color: #666666;
      font-weight: 600;
    }
  }
  .input-component {
    display: flex;
    flex-direction: column;
    &__control {
      display: flex;
      flex-direction: column;
      row-gap: 8px;
    }
    input {
      color: #666666;
      font-size: 16px;
      padding: 16px;
      border: 1px solid #cccccc;
      border-radius: 8px;
    }
    &._error {
      .input-component {
        input {
          border-color: #eb5757;
        }
        input::after {
          content: '';
          display: inline-block;
          width: 24px;
          height: 24px;
          background: url("../assets/icons/error.svg");
        }
      }
    }
  }
  .checkbox-component {
    &__control {
      display: flex;
      align-items: center;
      column-gap: 8px;
    }
  }
}
</style>
