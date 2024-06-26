<template>
  <section>
    <div class="title">신청 안내</div>
    <ul>
      <li v-for="item in descriptionList" :key="item.key">
        {{ item.key }} : {{ item.value }}
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      descriptionList: [
        { key: "배송 예정일", value: "7월 말" },
        { key: "가격", value: "50,000원 (배송료 포함)" },
        { key: "계좌", value: "카카오뱅크 3333-27-7758274 이은주" },
        { key: "발간", value: "청도 345kV 송전탑 반대 공동대책위원회" },
        { key: "문의", value: "053-290-7474" },
        { key: "신청 기한", value: "7월 7일 (일) 오후 12시까지" },
      ],
    };
  },
};
</script>

<style scoped>
section {
  width: var(--left-el-width);

  .title {
    margin-block-end: var(--size-min);
    font-size: var(--size-150);
  }

  ul {
    li {
      text-wrap: nowrap;

      &::before {
        content: "○";
        margin-inline-end: var(--size-min);
        font-weight: 200;
      }
    }
    margin-block-end: var(--size-000);
  }
}
</style>
