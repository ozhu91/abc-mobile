<template>
  <div class="audio-rec sub-font-color-1">
    <div class="icons-block">
      <img :src="this.icons.microfoneIcon" alt="recording" class="microfone" />
    </div>
    <div class="recoding-loader">
      <div
        v-bind:style="{ width: this.recordPercentage + '%' }"
        class="recoding-loader__line"
      ></div>
    </div>
    <span class="audio-rec__percentage">{{ getRecordPercentage }}%</span>
    <span>Запись сообщения</span>
  </div>
</template>

<script>
import microfone from "../../assets/icons/microfone.svg";

export default {
  props: {
    record: {
      type: Boolean,
    },
  },
  data() {
    return {
      recordPercentage: 0,
      interval: null,
      icons: {
        microfoneIcon: microfone,
      },
      isRecord: this.record,
    };
  },
  methods: {
    startRecording() {
      this.interval = setInterval(this.recording, 80);
    },
    recording() {
      if (this.recordPercentage === 100) {
        clearInterval(this.interval);
        this.isRecord = false;
        this.$emit("load", this.isRecord)
      } else {
        this.recordPercentage++;
      }
    },
  },
  computed: {
    getRecordPercentage() {
      return this.recordPercentage;
    },
  },
  mounted() {
    this.startRecording();
  },
};
</script>

<style>
.audio-rec {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  padding: 1.2rem;
  box-sizing: border-box;
}

.audio-rec .icons-block {
    margin-bottom: 1.4rem;
}

.recoding-loader {
  width: 100%;
  height: 4px;
  position: relative;
  background-color: cornsilk;
}

.recoding-loader__line {
  min-width: 0%;
  max-width: 100%;
  display: block;
  height: 4px;
  position: absolute;
  top: 0;
  left: 0;
  background-color: #f6c866;
}

.audio-rec__percentage {
    margin-top: 1.4rem;
  padding: 0.6rem;
}
</style>