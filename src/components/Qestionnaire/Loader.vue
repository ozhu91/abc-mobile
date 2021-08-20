<template>
  <div class="loader">
    <img :src="loaderIcon" alt="load" class="loader__icon spinnig" />
  </div>
</template>

<script>
import loader from "../../assets/icons/loader.svg";
export default {
  data() {
    return {
      loaderIcon: loader,
    };
  },
};
</script>

<style>
.loader {
  width: 100%;
  height: 100vh;
  max-height: 1024px;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  background-color: inherit;
}

.loader__icon {
  width: 73px;
  height: 73px;
}
</style>