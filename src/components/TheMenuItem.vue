<template>
  <li>
    <a :href="`#${link}`">{{ content }}</a>
  </li>
</template>

<script>
export default {
  props: ["content", "link"],
  data() {
    return {};
  },
};
</script>

<style scoped></style>
