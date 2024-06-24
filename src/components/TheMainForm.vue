<template>
  <form action="#" @submit.prevent="sendFormData">
    <template v-for="(item, key, index) in inputItems" :key="key">
      <button
        id="search-address"
        class="u-button"
        type="button"
        v-if="index === 2"
        @click="searchAddress"
      >
        주소 검색하기
      </button>
      <TheMainFormInput
        :id="key"
        :type="item.type"
        :keyName="item.keyName"
        :isRequired="item.required"
        :isDisabled="item.disabled"
        v-model="item.content"
      />
    </template>
    <TheMainFormSubmit :isFilledAll="isFilledAll" />
  </form>
</template>

<script>
import TheMainFormInput from "./TheMainFormInput.vue";
import TheMainFormSubmit from "./TheMainFormSubmit.vue";

export default {
  emits: ["submit-complete"],
  components: {
    TheMainFormInput,
    TheMainFormSubmit,
  },
  data() {
    return {
      inputItems: {
        name: { keyName: "이름", content: "", required: true },
        tel: { type: "tel", keyName: "전화번호", content: "", required: true },
        address: {
          keyName: "주소",
          content: "",
          required: true,
          disabled: true,
        },
        zonecode: {
          keyName: "우편번호",
          content: "",
          required: true,
          disabled: true,
        },
        subAddress: { keyName: "나머지 주소", content: "" },
        quantity: { keyName: "받을 권수", content: "", required: true },
        depositor: { keyName: "입금자명", content: "", required: true },
        email: { type: "email", keyName: "이메일", content: "" },
        etc: { type: "textarea", keyName: "남기고 싶은 말", content: "" },
      },
    };
  },
  methods: {
    searchAddress() {
      new daum.Postcode({
        oncomplete: (data) => {
          this.inputItems.address.content = data.address;
          this.inputItems.zonecode.content = data.zonecode;
        },
      }).open();
    },
    sendFormData() {
      const nameInputId = "entry.564802573";
      const telInputId = "entry.365965765";
      const zonecodeInputId = "entry.642965807";
      const addressInputId = "entry.88586585";
      const quantityInputId = "entry.228645623";
      const emailInputId = "entry.371759033";
      const etcInputId = "entry.542424423";
      const depositorInputId = "entry.1417473510";

      const nameUrl = nameInputId + "=" + this.inputItems.name.content;
      const telUrl = telInputId + "=" + this.inputItems.tel.content;
      const zonecodeUrl =
        zonecodeInputId + "=" + this.inputItems.zonecode.content;
      const addressUrl =
        addressInputId +
        "=" +
        `${this.inputItems.address.content} ${this.inputItems.subAddress.content}`;
      const quantityUrl =
        quantityInputId + "=" + this.inputItems.quantity.content;
      const depositorUrl =
        depositorInputId + "=" + this.inputItems.depositor.content;
      const emailUrl = emailInputId + "=" + this.inputItems.email.content;
      const etcUrl = etcInputId + "=" + this.inputItems.etc.content;

      const url = `https://docs.google.com/forms/d/e/1FAIpQLSf4fGa2NkEcZO2D75R50oGbqPEaMEFcl84qhPbS86SJg2Udkw/formResponse?${nameUrl}&${telUrl}&${zonecodeUrl}&${addressUrl}&${quantityUrl}&${depositorUrl}&${emailUrl}&${etcUrl}`;
      fetch(url)
        .then((res) => res.json())
        .then(this.$emit("submit-complete"));
    },
  },
  computed: {
    isFilledAll() {
      const requiredInputs = Object.values(this.inputItems).filter(
        (item) => item.required === true,
      );
      if (requiredInputs.some((item) => item.content === "")) return false;
      return true;
    },
  },
};
</script>

<style scoped>
form {
  width: var(--right-el-width);

  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: var(--size-500);
  row-gap: var(--size-100);

  #search-address {
    justify-self: start;
    background-color: var(--content-color);
    color: var(--gray-1);
    margin-block-start: var(--size-050);
  }
}
</style>
