<template>
  <section class="questionnaire__section">
    <Quote />
    <div class="popup" v-if="getAgeInterval">
      <div class="popup-wrapper">
        <span>{{ getAgeInterval }}</span>
      </div>
    </div>
    <h4 class="questionnaire__head sub-font-color-2">
      Запись, которую Вы услышите, может шокировать людей с неокрепшей психикой.
      Вы готовы узнать, что ждет именно Вас?
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
      Да
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
      Затрудняюсь ответить
    </button>
    <span class="question__number sub-font-color-1">Вопрос 5-5</span>
    <BackgroundIcons :icon="'eye'" />
    <BackgroundIcons />
  </section>
</template>

<script>
import Quote from "./Quote.vue";
import BackgroundIcons from "./BackgroundIcons.vue";

export default {
  props: {
    userAge: {
      type: Object,
      default: {},
    },
  },
  components: {
    Quote,
    BackgroundIcons,
  },
  data() {
    return {
      popupQuote: [
        "",
        "По вам скучает очень близкий человек, которого больше нет в мире живых.",
        "По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это дедушка или бабушка.",
        "По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это кто-то из Ваших родителей.",
      ],
      ageInterval: null,
      age: this.userAge,
    };
  },
  methods: {
    selectOption(val) {
      this.$emit("getValue", val);
    },
    calcAgeInterval() {
      let date = new Date(
        this.age.answears.year,
        this.age.answears.month - 1,
        this.age.answears.day
      );
      const dateNow = Date.now();
      let currentYear = dateNow - date;
      let oldest = Math.round(currentYear / (1000 * 60 * 60 * 24 * 365), 1);
      console.log(oldest);
      if (oldest < 18) {
        this.ageInterval = 0;
      } else if (oldest >= 18 && oldest < 35) {
        this.ageInterval = 1;
      } else if (oldest >= 35 && oldest < 46) {
        this.ageInterval = 2;
      } else if (oldest >= 46) {
        this.ageInterval = 3;
      } else return;
    },
  },
  computed: {
    getAgeInterval() {
      return this.popupQuote[this.ageInterval];
    },
  },
  mounted() {
    this.calcAgeInterval();
  },
};
</script>

<style>
.questionnaire__section {
  position: relative;
}

.popup {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 122px;
  padding: 1.2rem;
  box-sizing: border-box;
  font-size: 0.7rem;
  line-height: 1rem;
  font-family: "Bad Script", sans-serif;
  box-sizing: border-box;
}

.popup-wrapper {
  width: 100%;
  height: 100%;
  text-align: center;
  border-radius: 10px;
  background-color: #fff;
  color: #202024;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  font-size: 0.7rem;
  line-height: 1rem;
  position: relative;
  z-index: 5;
}

.popup-wrapper::after {
  content: "";
  position: absolute;
  bottom: -8px;
  right: 20px;
  width: 20px;
  height: 20px;
  transform: rotate(45deg);
  background-color: white;
}
</style>