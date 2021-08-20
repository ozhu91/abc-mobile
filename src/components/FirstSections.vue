<template>
  <div class="first-section section-padding">
      <div class="first-section__container">
        <img :src="images.hands" alt="hands" class="hands">
        <p class="text">
          Позвольте нам раскрыть эту волнующую тайну и 
            <br><span class="sub-font-color-2">с точностью определить дату и время вашей смерти,</span><br> а также предшествующую этому событию причину
        </p>
      </div>
      
  </div>
</template>

<script>
import hands from '../assets/images/hands.png';

export default {
  data() {
    return {
    images: {
      hands: hands
    }
    }
  }
}
</script>

<style scoped>
.first-section {
  margin-top: 42px;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
}

.first-section__container {
  position: relative;
  border: 1px solid #fff;
  border-radius: 3px;
  margin: 1.5rem;
  padding-top: calc(1rem + 42px);
  padding-bottom: 1rem;
  box-sizing: border-box;
  max-width: 442px;
}

.hands {
  position: absolute;
  top: -42px;
  left: calc(50% - 42px);
  height: 84px;
  width: 84px;
  object-position: center;
  object-fit: contain;
  z-index: 2;
}

.text {
  font-size: .8rem;
  line-height: 1.25rem;
  text-align: center;
  font-weight: 500;
  padding: .4rem 1.1rem;
}

.text span {
  font-size: 1rem;
}
</style>