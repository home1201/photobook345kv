<template>
  <div class="input-item" :data-key="id">
    <label :for="id">{{ keyName }}<sup v-if="isRequired">필수</sup></label>
    <input
      v-if="type !== 'textarea'"
      :type="type"
      :id="id"
      :name="id"
      :disabled="isDisabled"
      :required="isRequired"
      v-model="value"
    />
    <textarea
      v-else
      :id="id"
      :name="id"
      :disabled="isDisabled"
      :required="isRequired"
      v-model="value"
    ></textarea>
    <span v-if="isDisabled && value == ''">주소 검색하기를 클릭해주세요</span>
  </div>
</template>

<script>
export default {
  props: {
    id: String,
    keyName: String,
    modelValue: String,
    type: {
      type: String,
      default: "text",
    },
    isRequired: {
      type: Boolean,
      default: false,
    },
    isDisabled: {
      type: Boolean,
      default: false,
    },
  },
  emits: ["update:modelValue"],
  computed: {
    value: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit("update:modelValue", value);
      },
    },
    placeholder() {
      return this.isDisabled ? "주소 검색하기를 클릭해주세요" : "";
    },
  },
};
</script>

<style scoped>
.input-item {
  position: relative;

  label {
    display: block;

    sup {
      font-size: var(--size-050);
      color: var(--accent-color);
    }
  }

  input,
  textarea {
    width: 100%;
    padding: var(--size-min);
    background-color: var(--gray-0);
    border: 1px solid var(--gray-4);
    border-radius: var(--radius-min);

    &[disabled] {
      border: none;
      background-color: transparent;
      font-size: var(--size-100);
      padding: var(--size-min) 0;
    }
  }

  &[data-key="address"] {
    grid-column: span 2;
  }

  &[data-key="etc"] {
    grid-column: span 2;
  }

  span {
    position: absolute;
    left: 0;
    font-size: 0.9rem;
    color: var(--gray-6);
  }
}
</style>
