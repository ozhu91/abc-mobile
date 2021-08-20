<template>
  <form @submit="selectOption" class="questionnaire__section">
    <Quote />
    <h4 class="questionnaire__head sub-font-color-2">
      Укажите свою дату рождения:
    </h4>
    <select
      v-model="form.day"
      class="question__select"
      :style="{ backgroundImage: arrow }"
      size="1"
      required
      data-select="1"
    >
      <option disabled selected="selected" class="default-option" value="">
        День
      </option>
      <option v-for="n in 31" v-bind:key="n" :value="n">{{ n }}</option>
    </select>
    <select
      v-model="form.month"
      class="question__select"
      :style="{ backgroundImage: arrow }"
      size="1"
      required
      data-select="2"
    >
      <option disabled selected="selected" class="default-option" value="">
        Месяц
      </option>
      <option
        v-for="month in monthNames"
        v-bind:key="month.name"
        :value="month.id"
      >
        {{ month.value }}
      </option>
    </select>
    <select
      v-model="form.year"
      class="question__select"
      :style="{ backgroundImage: arrow }"
      size="1"
      required
      data-select="3"
    >
      <option disabled selected="selected" class="default-option" value="">
        Год
      </option>
      <option v-for="n in 120" v-bind:key="n" :value="2021 - n">
        {{ 2021 - n }}
      </option>
    </select>
    <input
      type="submit"
      class="
        question__button
        main-font-color
        sub-bg-color-2
      "
      value="Далее"
    />
    <span class="question__number sub-font-color-1">Вопрос 3-5</span>
    <BackgroundIcons :icon="'eye'" />
    <BackgroundIcons />
      

  </form>
</template>

<script>
import ArrowIcon from "../../assets/icons/arrow.svg";
import Quote from "./Quote.vue";
import BackgroundIcons from './BackgroundIcons.vue';

export default {
  components: {
    Quote,
    BackgroundIcons
  },
  data() {
    return {
      // quoteText:
      //   "Уже совсем скоро Вы узнаете много интересного о своем будущем!",
      options: [
      'foo',
      'bar',
      'baz'
    ],
      form: {
        day: "",
        month: "",
        year: "",
      },
      arrow: `url(${ArrowIcon})`,
      monthNames: [
        { id: 1, name: "Январь", value: "01" },
        { id: 2, name: "Февраль", value: "02" },
        { id: 3, name: "Март", value: "03" },
        { id: 4, name: "Апрель", value: "04" },
        { id: 5, name: "Май", value: "05" },
        { id: 6, name: "Июнь", value: "06" },
        { id: 7, name: "Июль", value: "07" },
        { id: 8, name: "Август", value: "08" },
        { id: 9, name: "Сентябрь", value: "09" },
        { id: 10, name: "Октябрь", value: "10" },
        { id: 11, name: "Ноябрь", value: "11" },
        { id: 12, name: "Декабрь", value: "12" },
      ],
    };
  },
  methods: {
    selectOption(e) {
            e.preventDefault();
      let isReady = true
      for(let item in this.form) {
        if(!item) {
          isReady = false
          return
        }
      }
      if(isReady) {
        this.$emit("getValue", this.form);
      } else {
        return 
      }
    },    
  },
};
</script>

<style>
.question__select {
  width: 179px;
  height: 40px;
  font-size: 0.7rem;
  border-radius: 50px;
  border: none;
  margin-top: 1rem;
  padding: 10px;
  position: relative;
  appearance: none;
  background-repeat: no-repeat;
  background-position: right;
  background-position-x: calc(100% - 10px);
  background-color: #cacacb;
  text-align-last: center;
}

.questionnaire__section select:focus {
  outline: none;
  border: 2px solid #e65152;
}

.questionnaire__section select:active {
  outline: none;
  border: 2px solid #e65152;
}

.questionnaire__section select:hover {
  cursor: pointer;
}

.questionnaire__section option {
  height: 100px;
}

.question__select option {
  width: 100%;
  max-width: 100%;
  text-align: center;
}

.default-option {
  pointer-events: none;
}

</style>