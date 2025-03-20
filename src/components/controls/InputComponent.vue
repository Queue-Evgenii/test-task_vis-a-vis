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
    },
    delay: {
      type: Number,
      default: 0,
    }
  },
  data() {
    return {
      timeout: null,
    }
  },
  methods: {
    debounce(callback) {
      clearTimeout(this.timeout);
      this.timeout = setTimeout(callback, this.delay);
    },
    handleChange(value) {
      this.debounce(() => this.$emit('update:value', value));
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
      <div class="input-component__container">
        <input
          type="text"
          :id="name"
          :placeholder="placeholder"
          :value="value"
          @input="handleChange($event.target.value)"
          class="input-component__input"
        >
      </div>
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
