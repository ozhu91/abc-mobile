<template>
  <div class="epic-quote">
    <img :src="icons.firstword" alt="firstword" class="runeword" />
    <p class="epic-quote__text">
      Вы, конечно, умрете.<br />
      И все, с кем вы знакомы, тоже однажды умрут.
    </p>
    <img :src="icons.secondword" alt="secondword" class="runeword" />
    <img :src="icons.earth" alt="earth" class="bg-icon earth" />
    <img :src="icons.eye" alt="eye" class="bg-icon eye" />
  </div>
</template>

<script>
import firstword from "../../assets/icons/firstword.svg";
import secondword from "../../assets/icons/secondword.svg";
import eye from "../../assets/icons/eye.svg";
import earth from "../../assets/icons/earth.svg";
export default {
  data() {
    return {
      icons: {
        firstword: firstword,
        secondword: secondword,
        earth: earth,
        eye: eye,
      },
    };
  },
};
</script>

<style>
.epic-quote {
  max-width: 1440px;
  width: 100%;
  text-align: center;
  font-family: "Bad Script", cursive;
  padding: 2rem 0;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  position: relative;
}

.runeword {
  height: 10px;
  object-position: center;
  object-fit: contain;
}

.epic-quote__text {
  margin: 1.75rem 0;
  padding: 0 2.1rem;
  font-size: 1rem;
  line-height: 1.4rem;
}

.bg-icon {
  position: absolute;
  object-fit: contain;
  object-position: center;
}

.bg-icon.earth {
  bottom: 1rem;
  left: -8px;
  width: 52px;
  height: 51px;
  opacity: 0.9;
}

.bg-icon.eye {
  top: 1rem;
  right: -25px;
  height: 44px;
  transform: rotate(-9.61deg);
  opacity: 0.4;
}
</style>