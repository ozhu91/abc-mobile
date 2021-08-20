<template>
      <img :src="this.eyeIcon" alt="eye" v-if="chooseIcon === 'eye'" class="background-icon background-icon_eye">
        <img :src="this.earthIcon" alt="earth" v-else class="background-icon background-icon_earth">
</template>

<script>
import eye from "../../assets/icons/eye.svg";
import earth from "../../assets/icons/earth.svg";

export default {
    props: {
        icon: {
            type: String,
            default: ""
        }
    },
    data() {
        return {
            earthIcon: earth,
            eyeIcon: eye,
            chooseIcon: this.icon
        }
    }

}
</script>

<style>
.background-icon {
  position: absolute;
  object-fit: contain;
  object-position: center;
}

.background-icon_earth {
  width: 51px;
  height: 51px;
  bottom: 37px;
  left: -10px;
}

.background-icon_eye {
  width: 84px;
  height: 44px;
  transform: rotate(-10deg);
  top: 67px;
  right: -30px;
}
</style>