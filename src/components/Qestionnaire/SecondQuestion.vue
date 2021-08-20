<template>
  <section class="questionnaire__section">
    <Quote :text="quoteText" />
    <h4 class="questionnaire__head sub-font-color-2">
      Когда Вы чувствуете себя наиболее комфортно?
    </h4>
    <button
      class="
        question__button
        main-font-color
        sub-bg-color-2
        fleckering
      "
      v-on:click="selectOption('Утро')"
    >
      Утро
    </button>
    <button
      class="
        question__button
        main-font-color
        sub-bg-color-2
        fleckering
      "
      v-on:click="selectOption('День')"
    >
      День
    </button>
    <button
      class="
        question__button
        main-font-color
        sub-bg-color-2
        fleckering
      "
      v-on:click="selectOption('Вечер')"
    >
      Вечер
    </button>
    <button
      class="
        question__button
        main-font-color
        sub-bg-color-2
        fleckering
      "
      v-on:click="selectOption('Ночь')"
    >
      Ночь
    </button>
    <span class="question__number sub-font-color-1">Вопрос 2-5</span>
    <BackgroundIcons :icon="'eye'" />
    <BackgroundIcons />
  </section>
</template>

<script>
import Quote from "./Quote.vue";
import BackgroundIcons from "./BackgroundIcons.vue";

export default {
  components: {
    Quote,
    BackgroundIcons,
  },
  data() {
    return {
      quoteText:
        "Мы расскажем Вам не только подробности вашей смерти, но также поможем Вам избежать этой ужасной даты и продлить вашу жизнь на многие годы.",
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