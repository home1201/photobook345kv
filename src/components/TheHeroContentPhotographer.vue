<template>
  <div class="title">참여작가</div>
  <div class="content">
    <span class="person-name" v-for="item in personList" :key="item">{{
      item
    }}</span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      personList: [
        "김민",
        "이재각",
        "정한결",
        "홍진휜",
        "이승훈",
        "장영식",
        "최형락",
        "어우기",
        "정운",
        "허란",
      ],
    };
  },
};
</script>

<style scoped>
.title {
  margin-block-start: var(--size-050);
  margin-block-end: var(--size-min);
  font-size: var(--size-150);
}
.content {
  text-wrap: wrap;
  width: 70%;

  .person-name {
    &:not(:last-child) {
      display: inline-block;
      margin-inline-end: var(--size-050);
    }
  }
}
</style>
