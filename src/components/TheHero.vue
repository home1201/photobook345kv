<template>
  <section :id="link" class="hero u-max-width u-pad-in-200">
    <TheHeroContent :mainLink="mainLink" />
    <img
      src="/assets/images/book_image.webp"
      :width="imgWidth"
      :height="imgHeight"
      alt=""
    />
  </section>
</template>

<script>
import TheHeroContent from "./TheHeroContent.vue";

export default {
  props: ["link", "mainLink"],
  components: {
    TheHeroContent,
  },
  data() {
    return {
      imgWidth: 880,
      imgHeight: 633,
    };
  },
};
</script>

<style scoped>
.hero {
  display: flex;
  flex-wrap: wrap-reverse;
  justify-content: center;

  row-gap: var(--size-050);
  column-gap: var(--column-gap);

  margin-block-start: var(--size-400);
  margin-inline: auto;

  img {
    aspect-ratio: v-bind(imgWidth) / v-bind(imgHeight);
    object-fit: contain;
    width: max(50%, 25rem);
  }
}
</style>
