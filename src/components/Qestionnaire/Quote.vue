<template>
  <div class="quote sub-font-color-1">
      <span>{{textInQuote}}</span>
  </div>
</template>

<script>
export default {
    props: {
        text: {
            type: String,
            default: "Уже совсем скоро Вы узнаете много интересного о своем будущем!"
        },
    },
    data() {
        return {
            textInQuote: this.text,
        }
    }
}
</script>

<style>

.quote {
  width: 100%;
  height: 122px;
  box-sizing: border-box;
  border-bottom: 1px solid #a6a6a7;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  font-size: .7rem;
  line-height: 1rem;
  font-family: "Bad Script", sans-serif;
}

.quote span {
    max-width: 235px;
    text-align: center;
}

</style>