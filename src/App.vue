<template>
  <template v-if="isNotCompleted">
    <TheMenu :links="links" />
    <TheHero :link="links.hero" :mainLink="links.main" />
    <TheMain :link="links.main" @submitComplete="submitComplete" />
  </template>
  <TheComplete v-else />
</template>

<script>
import TheHero from "./components/TheHero.vue";
import TheMenu from "./components/TheMenu.vue";
import TheMain from "./components/TheMain.vue";
import TheComplete from "./components/TheComplete.vue";

export default {
  components: {
    TheMenu,
    TheHero,
    TheMain,
    TheComplete,
  },
  data() {
    return {
      isNotCompleted: true,
      links: {
        hero: "hero",
        main: "main",
      },
    };
  },
  methods: {
    submitComplete() {
      this.isNotCompleted = false;
    },
  },
};
</script>

<style>
body {
  --main-color: var(--gray-1);
  --content-color: var(--gray-9);
  --accent-color: #c70b0c;

  --left-el-width: 25rem;
  --right-el-width: max(50%, 25rem);

  --row-gap: var(--size-050);
  --column-gap: var(--size-300);

  font-family: "Wanted Sans Variable", system-ui, sans-serif;
  background-color: var(--main-color);
  margin-block-end: var(--size-700);
}
</style>
