<template>
  <main :id="link" class="u-max-width u-pad-in-200">
    <TheMainDesc />
    <TheMainForm @submitComplete="submitComplete" />
  </main>
</template>

<script>
import TheMainForm from "./TheMainForm.vue";
import TheMainDesc from "./TheMainDesc.vue";

export default {
  props: ["link"],
  emits: ["submit-complete"],
  components: {
    TheMainForm,
    TheMainDesc,
  },
  methods: {
    submitComplete() {
      this.$emit("submit-complete");
    },
  },
};
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  column-gap: var(--column-gap);
  row-gap: var(--row-gap);

  margin-inline: auto;
  margin-block-start: var(--size-350);
}
</style>
