<script>
import ButtonComponent from './controls/ButtonComponent.vue';
import CheckboxComponent from './controls/CheckboxComponent.vue';
import InputComponent from './controls/InputComponent.vue';
import { useForm, useField } from "vee-validate";
import { reactive, ref, watch } from "vue";

export default {
  name: "OrderFormComponent",
  components: {
    InputComponent,
    CheckboxComponent,
    ButtonComponent,
  },
  setup() {
    const orderData = reactive({
      first_name: useField("first_name", (value) => {
        const errors = [];
        if (!value) errors.push("Поле обов’язкове");
        if (!/^[А-Яа-яЁёІіЇїЄєҐґ'’-]+$/.test(value))
          errors.push("Тільки кирилиця, апостроф та мінус всередині слова");
        if (!value || value.length < 1 || value.length > 38)
          errors.push("Не менше 1 та не більше 38 симовлів");
        return errors;
      }),
      last_name: useField("last_name", (value) => {
        const errors = [];
        if (!value) errors.push("Поле обов’язкове");
        if (!/^[А-Яа-яЁёІіЇїЄєҐґ'’-]+$/.test(value))
          errors.push("Тільки кирилиця, апостроф та мінус всередині слова");
        if (!value || value.length < 1 || value.length > 38)
          errors.push("Не менше 1 та не більше 38 симовлів");
        return errors;
      }),
      sum: useField("sum", (value) => {
        const errors = [];
        if (!value) return errors;
        if (!/^\d+$/.test(value)) errors.push("Тільки числа");
        if (value < 1000 || value > 1000000) errors.push("Сума від 1000 до 1 000 000");
        return errors;
      }),
      itn: useField("itn", (value) => {
        const errors = [];
        if (!value) errors.push("Поле обов’язкове");
        if (!/^\d{8,10}$/.test(value)) errors.push("Тільки цифри (8-10 символів)");
        return errors;
      }),
      isAgreed: useField("isAgreed", (value) => {
        const errors = [];
        if (!value) errors.push("Поле обов’язкове");
        return errors;
      }),
    });

    const handleSubmit = async () => {
      for (const field of Object.values(orderData)) {
        const res = await field.validate();

        if (res.errors.length > 0) {
          console.log("Invalid", "Validation failed for:", field);
          return;
        }
      }

      const formValues = Object.keys(orderData).reduce((acc, key) => {
        acc[key] = orderData[key].value;
        return acc;
      }, {});
      
      console.log("Valid", formValues);
    };

    return {
      orderData,
      handleSubmit,
    };
  },
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
          :delay="1000"
          :value="orderData.first_name.value"
          @update:value="value => orderData.first_name.handleChange(value)"
          :errors="orderData.first_name.errors"
        />
        <InputComponent
          name="Прізвище"
          placeholder="Введіть прізвище"
          :delay="1000"
          :value="orderData.last_name.value"
          @update:value="value => orderData.last_name.handleChange(value)"
          :errors="orderData.last_name.errors"
        />
        <InputComponent
          name="Сума угоди"
          placeholder="Введіть суму угоди"
          :delay="1000"
          :value="orderData.sum.value"
          @update:value="value => orderData.sum.handleChange(value)"
          :errors="orderData.sum.errors"
        />
        <InputComponent
          name="Іпн"
          placeholder="Введіть іпн"
          :delay="1000"
          :value="orderData.itn.value"
          @update:value="value => orderData.itn.handleChange(value)"
          :errors="orderData.itn.errors"
        />
        <CheckboxComponent
          name="Погоджуюсь з правилами та умовами"
          :delay="1000"
          :value="orderData.isAgreed.value"
          @update:value="value => orderData.isAgreed.handleChange(value)"
          :errors="orderData.isAgreed.errors"
        />
        <div class="form-order__submit">
          <ButtonComponent class="_button-1" @clickHoisting="handleSubmit">Відправити</ButtonComponent>
        </div>
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
      width: 100%;
    }
    &._error {
      .input-component__input {
        border-color: #eb5757;
      }
      .input-component__container {
        position: relative;
        &::after {
          content: url("../assets/icons/error.svg");
          display: inline-block;
          position: absolute;
          width: 24px;
          height: 24px;
          top: calc(50% - 12px);
          right: 12px;
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
  &__submit {
    margin: 0 auto;
    max-width: 172px;
  }
}
</style>
