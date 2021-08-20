<template>
  <div class="header">
    <div class="header-wrapper-blik section-padding">
      <img :src="images.blik" alt="blik" class="blik" />
      <div class="banner">
        <span class="sub-font-color-1"
          >Лучшие астрологи и экстрасенсы Румынии</span
        >
        <hr class="banner__line sub-font-color-1" />
        <span class="sub-font-color-1">Точность прогноза: 97%</span>
      </div>
      <div class="composition">
        <div class="composition__ornament-block">
          <img
            :src="icons.ornament"
            alt="ornament"
            class="composition__ornament"
          />
          <img :src="images.woman" alt="women" class="composition__women" />
        </div>
      </div>
      <p class="question sub-font-color-2">
        Вас беспокоит вопрос о том, <br /><span>
          когда Вы покинете этот Мир и при каких обстоятельствах?</span
        >
      </p>
    </div>
    <button class="question__button main-font-color sub-bg-color-2 fleckering">Да</button>
    <button class="question__button main-font-color sub-bg-color-2 fleckering">Нет</button>

    <span class="desk sub-font-color-1">Онлайн предсказание</span>
  </div>
</template>

<script>
import blik from "../assets/images/blik.png";
import woman from "../assets/images/woman1.png";
import ornament from "../assets/icons/ornament.svg";

export default {
  data() {
    return {
      images: {
        blik: blik,
        woman: woman,
      },
      icons: {
        ornament: ornament,
      },
    };
  },
};
</script>

<style scoped>
.header {
  width: 100%;
  /* min-height: 100vh; */
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  box-sizing: border-box;
  overflow: hidden;
}

.header-wrapper-blik {
  width: 100%;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  box-sizing: border-box;
  position: relative;
}

.blik {
  position: absolute;
  top: 0;
  left: -20px;
  max-height: 100%;
  min-width: calc(100% + 20px);
  object-fit: cover;
  object-position: center;
  z-index: 2;
}

.banner {
  width: 100%;
  box-sizing: border-box;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
}

.banner__line {
  width: 100%;
}

.banner span:first-child {
  font-size: 0.6rem;
}

.banner span:last-child {
  padding: 0px;
  margin: 0px;
}

.composition {
  width: 100%;
  margin: 1.85rem 0 0.65rem 0;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
}

.composition__ornament-block {
  width: 200px;
  height: 200px;
  position: relative;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  padding: 30px;
  box-sizing: border-box;
}

.composition__women {
  width: 100%;
  object-fit: contain;
  object-position: center;
  z-index: 3;
}

.composition__ornament {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  object-fit: contain;
  object-position: center;
  z-index: 1;
}

.question {
  font-size: 0.8rem;
  line-height: 1.25rem;
  width: 100%;
  text-align: center;
  padding: 0 1rem;
  box-sizing: border-box;
  max-width: 500px;
}

.question span {
  text-transform: uppercase;
}

.question__button {
  width: 179px;
  height: 40px;
  font-size: 0.7rem;
  border-radius: 50px;
  border: none;
  margin-top: 1rem;
  position: relative;
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

.desk {
  margin-top: 1rem;
  font-size: 0.6rem;
  line-height: 0.7rem;
}
</style>