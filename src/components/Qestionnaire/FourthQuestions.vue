<template>
  <section class="questionnaire__section">
    <Quote />
    <h4 class="questionnaire__head sub-font-color-2">
      Снятся ли вам умершие люди?
    </h4>
    <button class="question__button main-font-color sub-bg-color-2 fleckering" v-on:click="selectOption('Да')">
      Да
    </button>
    <button class="question__button  main-font-color sub-bg-color-2 fleckering" v-on:click="selectOption('Нет')">
      Нет
    </button>
    <button class="question__button main-font-color sub-bg-color-2 fleckering" v-on:click="selectOption('Иногда')">
      Иногда
    </button>
    <span class="question__number sub-font-color-1">Вопрос 4-5</span>
    <BackgroundIcons :icon="'eye'" />
    <BackgroundIcons />
  </section>
</template>

<script>
import Quote from "./Quote.vue";
import BackgroundIcons from "./BackgroundIcons.vue"

export default {
  components: {
    Quote,
    BackgroundIcons
  },
  data() {
    return {

    };
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