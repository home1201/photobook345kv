<template>
  <div class="submit">
    <button type="submit" class="u-button" :disabled="isUnfilledAny">
      제출하기
    </button>
    <span v-if="isUnfilledAny">필수 항목을 모두 채워주세요!</span>
  </div>
</template>

<script>
export default {
  props: { isFilledAll: Boolean },
  computed: {
    isUnfilledAny() {
      return this.isFilledAll === false;
    },
  },
};
</script>

<style scoped>
.submit {
  grid-column: span 2;
  position: relative;

  button {
    background-color: var(--content-color);
    color: var(--gray-1);

    &[disabled] {
      color: var(--gray-3);
      background-color: var(--gray-5);
    }
  }

  span {
    position: absolute;
    bottom: -2rem;
    left: 0;

    color: var(--accent-color);
  }
}
</style>
