<template>
  <section>
    <TheHeroContentHeading />
    <p>
      그 날을 증언한 현장의 사진! 청도 삼평리 345kv 송전탑 공사강행 10년을 맞아,
      송전탑 반대를 외쳤던 우리의 목소리는 무엇을 기억하고 무엇을 다시 되살려야
      하는지 살펴보고자 사진집
      <strong class="title">‘삼평리에 평화를 (가제)’</strong>를 발간합니다. 그
      날을 기억하고 함께 하는 연대의 마음으로, 많은 신청 부탁드립니다.
    </p>
    <strong class="notice"
      >사진집 판매 수익금 전액은 청도 삼평리 송전탑 반대 운동에
      사용됩니다.</strong
    >
    <TheHeroContentPhotographer />
    <a :href="`#${mainLink}`" class="cta u-button">사진집 신청하기</a>
  </section>
</template>

<script>
import TheHeroContentHeading from "./TheHeroContentHeading.vue";
import TheHeroContentPhotographer from "./TheHeroContentPhotographer.vue";

export default {
  props: ["mainLink"],
  components: {
    TheHeroContentHeading,
    TheHeroContentPhotographer,
  },
};
</script>

<style scoped>
section {
  --content-color: var(--gray-9);

  width: 25rem;
  color: var(--content-color);

  p {
    margin-block-start: var(--size-050);
    .title {
      font-weight: 700;
    }
  }

  .notice {
    display: block;
    margin-block-start: var(--size-050);
  }

  .cta {
    font-size: var(--size-100);
    background-color: var(--content-color);
    margin-block-start: var(--size-100);

    &,
    &:link,
    &:visited {
      color: var(--gray-1);
    }
  }
}
</style>
