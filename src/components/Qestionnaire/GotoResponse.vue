<template>
  <div class="go-to-response sub-font-color-1" v-if="!callAndListen">
    <div class="go-to-response__head">
      <p class="go-to-response__head-popup">
        <span>Спасибо за ваши ответы!</span><b>{{ getGoToPopup }}</b>
      </p>
    </div>
    <p class="go-to-response__instructions go-to-response__instructions_first">
      Вы можете узнать, как повлиять на события, которые ожидают вас в ближайшем
      будущем.
    </p>

    <div class="go-to-response__main-message sub-font-color-2">
      <p>
        <b>Первое значимое событие может произойти уже 14.02.2021,</b>
        Вам надо быть готовым, что бы последствия не оказались необратимыми.
      </p>
    </div>

    <p class="go-to-response__instructions">
      Нажмите на кнопку ниже прямо сейчас и наберите наш номер телефона.
      Прослушайте важную информацию!
    </p>
    <button class="get-response fleckering" v-on:click="getToResponse()">
      Позвонить и прослушать
    </button>
    <Footer />
  </div>
  <div class="response-call" v-else>
    <div class="starwars">
      <div class="starwars__text scrolling" id="starwars__text">
        <h5>{{ getResponseData.name }}</h5>
        <div class="starwars__content">
          <h6>Basic data of a person</h6>
          <div>Height: {{ getResponseData.mass }}</div>
          <div>Mass: {{ getResponseData.mass }}</div>
          <div>Color hair: {{ getResponseData.hair_color }}</div>
          <div>Color skin: {{ getResponseData.skin_color }}</div>
          <div>Color eyes: {{ getResponseData.eye_color }}</div>
          <div>Birth_year: {{ getResponseData.birth_year }}</div>
          <div>Gender: {{ getResponseData.gender }}</div>
          <div>
            Homeworld: <a :href="getResponseData.homeworld" target="_blank"></a
            >{{ getResponseData.homeworld }}
          </div>
        </div>
        <div class="starwars__content">
          <h6>Favorite movies</h6>
          <div v-if="getResponseData.films.length">
            <span v-for="film in getResponseData.films" :key="film"
              ><a :href="film" target="_blank"></a> {{ film }}</span
            >
          </div>
          <span v-else>Unknown</span>
        </div>
        <div class="starwars__content">
          <h6>Species</h6>
          <div v-if="getResponseData.species.length">
            <span v-for="spec in getResponseData.species" :key="spec">{{
              spec
            }}</span>
          </div>
          <span v-else>Unknown</span>
        </div>
        <div class="starwars__content">
          <h6>Vehicles</h6>
          <div v-if="getResponseData.vehicles.length">
            <span v-for="vehicle in getResponseData.vehicles" :key="vehicle"
              ><a :href="vehicle" target="_blank"></a> {{ vehicle }}</span
            >
          </div>
          <span v-else>Unknown</span>
        </div>
        <div class="starwars__content">
          <h6>Starships</h6>
          <div v-if="getResponseData.films.length">
            <span v-for="starship in getResponseData.starships" :key="starship"
              ><a :href="starship" target="_blank"></a> {{ starship }}</span
            >
          </div>
          <span v-else>Unknown</span>
        </div>
        <div class="starwars__description">
          <span>{{ getResponseData.created }}</span>
          <span>{{ getResponseData.edited }}</span>
          <span>{{ getResponseData.edited }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Footer from "./Footer.vue";
export default {
  components: {
    Footer,
  },
  data() {
    return {
      goToPopup:
        "Мы подготовили для Вас персональную аудио запись с Вашим прогнозом.",
      callAndListen: false,
      responseData: null,
      error: null,
    };
  },
  methods: {
    async getToResponse() {
      let data;
      await fetch("https://swapi.dev/api/people/1")
        .then((res) => res.json())
        .then((json) => (data = json))
        .catch((e) => {
          this.error = "Ошибка при получении данных: " + e;
        });

      this.responseData = data;
      console.log(data);
      this.callAndListen = !this.callAndListen;
    },
  },
  computed: {
    getGoToPopup() {
      return this.goToPopup;
    },
    getResponseData() {
      return this.responseData;
    },
  },
};
</script>

<style>
.go-to-response {
  width: 100%;
  height: 100vh;
  padding-top: 1rem;
  display: flex;
  flex-flow: column;
  justify-content: space-between;
  align-items: center;
  box-sizing: border-box;
  overflow: hidden;
  font-size: 0.7rem;
  line-height: 0.8rem;
}

.go-to-response__head {
  height: 124px;
  position: relative;
  width: 80%;
  box-sizing: border-box;
}

.go-to-response__head-popup {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 15px;
  background-color: white;
  color: #202024;
  line-height: 0.9rem;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
}

.go-to-response__head-popup::after {
  content: "";
  position: absolute;
  bottom: -8px;
  right: 20px;
  width: 20px;
  height: 20px;
  transform: rotate(45deg);
  background-color: white;
}

.go-to-response__head-popup span {
  padding: 0;
  margin: 0;
}

.go-to-response__instructions {
  width: 233px;
  padding: 0;
  margin: 0;
}

.go-to-response__instructions_first {
  width: 219px;
}

.go-to-response__main-message {
  max-width: 480px;
  margin: 0 1.5rem;
  border: 1px solid white;
  font-size: 0.8rem;
  line-height: 1.25rem;
  padding: 0.8rem;
  box-sizing: border-box;
}

.go-to-response__main-message b {
  text-transform: uppercase;
}

@media (min-width: 1440px) {
  .go-to-response__main-message {
    padding: 1.5rem;
  }
}

.get-response {
  width: 238px;
  height: 48px;
  font-size: 0.7rem;
  position: relative;
  overflow: hidden;
  border: none;
  color: white;
  border-radius: 50px;
  background: linear-gradient(
    90deg,
    rgba(76, 217, 100, 0.9) -6.2%,
    rgba(50, 185, 73, 0.9) 100%
  );
}

.get-response::before {
  content: "";
  display: block;
  position: absolute;
  top: 0px;
  left: 0px;
  height: 48px;
  width: 116px;
  background: linear-gradient(
    248.67deg,
    rgba(255, 255, 255, 0) 30.84%,
    rgba(255, 255, 255, 0.29) 46.06%,
    rgba(255, 255, 255, 0) 64.04%
  );
  z-index: 99;
}

.response-call {
  width: 100%;
  height: 100vh;
  max-height: 100vh;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  overflow: hidden;
  perspective-origin: 50% 50%;
  perspective: 250px;
}

.starwars {
  width: 80%;
  height: 100vh;
  overflow-y: hidden;
  transform: rotateX(30deg);
}

.starwars::-webkit-scrollbar {
  width: 0;
}

.starwars__text {
  margin-top: 100vh;
  min-height: 100vh;
  font-size: 0.8rem;
  letter-spacing: 0.3rem;
  line-height: 1.6rem;
}

.starwars__text h5 {
  font-size: 1.4rem;
  margin-bottom: 3rem;
}

.starwars__text h6 {
    display: inline-block;
    width: 100%;
  font-size: 1.1rem;
  margin-bottom: 1rem;
  text-align: center;
}

.starwars__content {
    margin-top: 2rem;
    display: flex;
    flex-flow: column;
    justify-content: flex-start;
    align-items: center;
}


</style>