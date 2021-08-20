<template>
  <div id="app" class="main-bg-color main-font-color">
    <Header />
    <FirstSections />
    <SecondSection />
    <Questionnaire />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import FirstSections from './components/FirstSections.vue'
import SecondSection from './components/SecondSection.vue'
import Questionnaire from './components/Qestionnaire/Questionnaire.vue'


export default {
  name: 'App',
  components: {
    Header,
    FirstSections,
    SecondSection,
    Questionnaire
  }
}
</script>

<style>

@import "./assets/styles/reset.css";
@import "./assets/styles/variables.css";
@import "./assets/styles/animations.css";


html {
  font-size: 20px;
}

body {
  font-family: "Roboto", sans-serif;
}

#app {
  width: 100%;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  overflow: hidden;
}

</style>
