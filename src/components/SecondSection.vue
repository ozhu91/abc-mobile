<template>
  <div class="second-section" :class="{'showing': visible}" :style="images.backgroundStyle">
    <p class="text">
      Многие не верят предсказаниям и мы решили доказать каждому,
      <br />
      <span class="sub-font-color-2">
        что прогноз может изменить жизнь любого человека!
      </span>
    </p>
  </div>
</template>

<script>
import bg from "../assets/images/bg_section2.jpg";

export default {
  data() {
    return {
      images: {
        backgroundStyle: {
          backgroundImage: `url(${bg})`,
          backgroundPosition: "center",
          backgroundRepeat: "no-repeat",
        },
      },
      visible: false,
      offsetPosition: null,
      offsetHeight: null
    };
  },
  methods: {
      showSection() {
        if(window.scrollY  > (this.offsetPosition - this.offsetHeight) ) {
          this.visible = true
        } 
      },
        
        

    },
    computed: {
      isVisible() {
        return this.visible
      }
    },
    mounted() {
      const section = document.querySelector(".second-section")
      this.offsetPosition = section.offsetTop
            this.offsetHeight = section.offsetHeight

      document.addEventListener('scroll', () => {
        this.showSection()
      })
    }
};
</script>

<style scoped>
.second-section {
  max-width: 1440px;
  width: 100%;
  padding: 2.5rem;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  position: relative;
  box-sizing: border-box;
  overflow: hidden;
  background-size: cover;
  min-height: calc(100vw * 0.4);
  visibility: hidden;
}

.second-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: .7;
  z-index: 1;
  background-color: rgba(0, 0, 0, 1);
}

.text {
  font-size: 0.8rem;
  line-height: 1.25rem;
  letter-spacing: 1px;
  z-index: 2;
  font-weight: 400;
  width: 100%;
  text-align: center;
  box-sizing: border-box;
  max-width: 380px;
}

.text span {
  font-size: 1rem;
}

@media (min-width: 1440px) {
  .text {
    font-size: 1.25rem;
  }

  .text span {
    font-size: 1.25rem;
  }
}
</style>