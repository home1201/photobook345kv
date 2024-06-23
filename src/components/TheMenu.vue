<template>
  <header>
    <div class="title">
      <strong>'삼평리에 평화를'</strong>
      사진집 예약
    </div>
    <ul>
      <TheMenuItem
        v-for="item in menuItems"
        :key="item.id"
        :link="item.id"
        :content="item.text"
      />
    </ul>
  </header>
</template>

<script>
import TheMenuItem from "./TheMenuItem.vue";
export default {
  props: ["links"],
  components: {
    TheMenuItem,
  },
  data() {
    return {
      menuItems: [
        { id: this.links.hero, text: "사진집 소개" },
        { id: this.links.main, text: "신청하기" },
      ],
      css: {
        mobileSizePx: 420,
      },
    };
  },
  computed: {
    mobileSizeEM() {
      return this.css.mobileSizePx / 16 + "em";
    },
  },
};
</script>

<style scoped>
header {
  position: sticky;
  top: 0;

  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  column-gap: 2vw;
  row-gap: var(--size-000);
  width: 100svw;

  padding-block: var(--size-050);
  font-size: var(--size-150);
  border-block-end: 0.5px solid var(--gray-5);
  background-color: var(--main-color);
  color: var(--content-color);

  .title {
    margin-inline: var(--size-100);
    font-weight: 600;

    strong {
      display: inline-block;
      font-family: "JalnanGothic";
      font-weight: 400;
      transform: translateY(1px);
      margin-inline-end: var(--size-min);
    }
  }

  ul {
    text-wrap: nowrap;

    & > * {
      --item-border: 0.3px solid var(--gray-4);

      display: inline-block;
      border-inline-end: var(--item-border);
      padding-inline: var(--size-100);
      text-wrap: nowrap;

      &:first-child {
        border-inline-start: var(--item-border);
      }
    }
  }
}
</style>
