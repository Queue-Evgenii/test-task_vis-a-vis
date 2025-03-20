<script>
export default {
  props: {
    value: {
      type: Boolean,
      required: true,
    },
    name: {
      type: String,
      default: "",
    },
    errors: {
      type: Array,
      default: [],
    }
  },
};
</script>


<template>
  <div :class="['checkbox-component', errors.length > 0 ? '_error' : '']">
    <div class="checkbox-component__control">
      <input
        type="checkbox"
        :id="name"
        :checked="value"
        @change="$emit('update:value', $event.target.checked)"
      />
      <label
        v-if="name"
        :for="name"
        class="checkbox-component__label"
      >
        {{ name }}
      </label>
    </div>
    
    <ul v-if="errors.length > 0" class="checkbox-component__errors">
      <li
        v-for="(error, index) in errors"
        :key="index"
        class="checkbox-component__error"
      >
        {{ error }}
      </li>
    </ul>
  </div>
</template>
