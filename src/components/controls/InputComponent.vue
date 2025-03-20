<script>
export default {
  name: "InputComponent",
  props: {
    name: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
    value: {
      type: String,
      required: true,
    },
    errors: {
      type: Array,
      default: [],
    }
  }
}
</script>

<template>
  <div :class="['input-component', errors.length > 0 ? '_error' : '']">
    <div class="input-component__control">
      <label
        v-if="name"
        :for="name"
        class="input-component__label"
      >
        {{ name }}
      </label>
      <input
        type="text"
        :id="name"
        :placeholder="placeholder"
        :value="value"
        @input="$emit('update:value', $event.target.value)"
        class="input-component__input"
      >
    </div>
    <ul v-if="errors.length > 0" class="input-component__errors">
      <li
        v-for="(error, index) in errors"
        :key="index"
        class="input-component__error"
      >
        {{ error }}
      </li>
    </ul>
  </div>
</template>
