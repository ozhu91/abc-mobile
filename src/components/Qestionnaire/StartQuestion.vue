<template>
  <section class="questionnaire__section">
    <h4 class="questionnaire__head sub-font-color-2">Боитесь ли вы умереть?</h4>
    <button
      class="
        question__button 
        main-font-color
        sub-bg-color-2
        fleckering
      "
      v-on:click="selectOption('Да')"
    >
      Да
    </button>
    <button
      class="
        question__button
        main-font-color
        sub-bg-color-2
        fleckering
      "
      v-on:click="selectOption('нет')"
    >
      Нет
    </button>
    <span class="question__number sub-font-color-1 ">Вопрос 1-5</span>
    <EpicQuote />
  </section>
</template>
<script>
import EpicQuote from "./EpicQuote.vue";
import Footer from "./Footer.vue";


export default {
  components: {
    EpicQuote,
    Footer,
  },
  methods: {
    selectOption(val) {
      this.$emit("getValue", val);
    },
  },
};
</script>

<style>

</style>