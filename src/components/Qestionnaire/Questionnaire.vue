<template>
  <div class="questionnaire" :class="{'showing': visible}" v-if="!isLoading">
    <StartQuestion
      v-if="getQuestionCurrent === 1 && !isPassed"
      @getValue="getValue($event, 1)"
    />
    <SecondQuestion
      v-if="getQuestionCurrent === 2"
      @getValue="getValue($event, 2)"
    />
    <ThirdQuestion
      v-if="getQuestionCurrent === 3"
      @getValue="getValue($event, 3)"
    />
    <FourthQuestions
      v-if="getQuestionCurrent === 4"
      @getValue="getValue($event, 4)"
    />
    <FifthQuestion
      v-if="getQuestionCurrent === 5 && !isPassed"
      @getValue="getValue($event, 5)"
      :userAge="getQuestions[2]"
    />
    <AudioRec
      v-if="isPassed && recording"
      @load="checkLoadResponse"
      :record="recording"
    />
    <GotoResponse v-if="getResponse" />
  </div>
  <Loader v-else />
</template>

<script>
import StartQuestion from "./StartQuestion.vue";
import SecondQuestion from "./SecondQuestion.vue";
import ThirdQuestion from "./ThirdQuestion.vue";
import FourthQuestions from "./FourthQuestions.vue";
import FifthQuestion from "./FifthQuestion.vue";
import AudioRec from "./AudioRec.vue";
import GotoResponse from "./GotoResponse.vue";
import Loader from "./Loader.vue";

export default {
  components: {
    StartQuestion,
    SecondQuestion,
    ThirdQuestion,
    FourthQuestions,
    FifthQuestion,
    AudioRec,
    GotoResponse,
    Loader,
  },
  data() {
    return {
      questions: [
        {
          id: 1,
          answears: null,
        },
        {
          id: 2,
          answears: null,
        },
        {
          id: 3,
          answears: null,
        },
        {
          id: 4,
          answears: null,
        },
        {
          id: 5,
          answears: null,
        },
      ],
      questionCurrent: 1,
      passed: false,
      load: false,
      recording: false,
      response: null,
      visible: false,
      offsetPosition: null,
      offsetHeight: null
    };
  },
  methods: {
    loading(isLoad = false) {
      this.load = isLoad;
    },
    getValue(val, id) {
      let quest = this.questions.find((item) => item.id === id);
      quest.answears = val;
      if (id < 5) {
        this.loading(true);
        this.questionCurrent++;
        setTimeout(this.loading, 500);
      } else if (id === 5) {
        this.loading(true);
        this.passed = true;
        this.recording = true;
        this.questionCurrent = 1;
        setTimeout(this.loading, 500);
      } else {
        return;
      }
    },
    checkLoadResponse(event) {
      this.recording = false;
      this.response = !event;
    },
    showSection() {
        if(window.scrollY  > (this.offsetPosition - this.offsetHeight) ) {
          this.visible = true
        } 
      },
  },
  computed: {
    getQuestionCurrent() {
      return this.questionCurrent;
    },
    isPassed() {
      return this.passed;
    },
    getQuestions() {
      return this.questions;
    },
    isLoading() {
      return this.load;
    },
    getResponse() {
      return this.response;
    },
    isVisible() {
        return this.visible
      }
  },
  mounted() {
      const section = document.querySelector(".questionnaire")
      this.offsetPosition = section.offsetTop
      this.offsetHeight = section.offsetHeight

      document.addEventListener('scroll', () => {
        this.showSection()
      })
    }
};
</script>

<style>
.questionnaire {
  width: 100%;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  box-sizing: border-box;
  text-align: center;
  padding-top: 0.5rem;
  height: 100vh;
  box-sizing: border-box;
  max-height: 1024px;
  max-width: 1440px;
  visibility: hidden;
}

.questionnaire__section {
  width: 100%;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  box-sizing: border-box;
  text-align: center;
  position: relative;
}

.questionnaire__head {
  text-transform: uppercase;
  font-size: 0.8rem;
  margin-bottom: 0.4rem;
}

.question__button {
  width: 179px;
  height: 40px;
  font-size: 0.7rem;
  border-radius: 50px;
  border: none;
  margin-top: 1rem;
  position: relative;
  overflow: hidden;
}

.question__button::before {
  content: "";
  display: block;
  position: absolute;
  top: 0px;
  height: 40px;
  width: 87px;
  background: linear-gradient(
    220.67deg,
    rgba(255, 255, 255, 0) 30.84%,
    rgba(255, 255, 255, 0.29) 46.06%,
    rgba(255, 255, 255, 0) 64.04%
  );
  z-index: 99;
}

.question__button:last-of-type {
  margin-bottom: 1rem;
}

.question__number {
  font-size: 0.6rem;
}

.questionnaire__head {
  margin-top: 1rem;
  padding-bottom: 1rem;
  padding: 0.8rem;
  line-height: 1.25rem;
}

.question__number {
  padding-top: 1.3rem;
  padding-bottom: 2.4rem;
}
</style>