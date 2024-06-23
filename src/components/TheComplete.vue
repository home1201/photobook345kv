<template>
  <div class="complete">
    <img
      src="/assets/images/book_image.webp"
      :width="imgWidth"
      :height="imgHeight"
      alt=""
    />
    <p>사진집을 신청해주셔서 감사합니다.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgWidth: 880,
      imgHeight: 633,
    };
  },
};
</script>

<style scoped>
.complete {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-block-start: var(--size-800);

  img {
    aspect-ratio: v-bind(imgWidth) / v-bind(imgHeight);
    object-fit: contain;
    width: 25rem;
  }

  p {
    font-size: var(--size-200);
    padding-block-start: var(--size-100);
  }
}
</style>
