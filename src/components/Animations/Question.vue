<template>
  <div class="card">
    <div class="card-body">
      <h2 v-text="question"></h2>
      <form class="form form-inline" @submit.prevent="checkResult">
        <input
          class="form-control mr-2"
          type="text"
          placeholder="Resposta"
          v-model="response"
        />
        <button type="submit" class="btn btn-success btn-md rounded-0">
          Responder
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: "Gerando pergunta...",
      result: 0,
      response: ""
    };
  },
  created() {
    this.generateQuestion();
  },
  methods: {
    generateQuestion() {
      let firstNumber = this.generanteRandomNumber(1, 100);
      let secondNumber = this.generanteRandomNumber(1, 100);

      this.result = firstNumber + secondNumber;

      this.question = `Qual é o resultado da soma entre ${firstNumber} + ${secondNumber}?`;
    },

    generanteRandomNumber(minValue, maxValue) {
      return Math.round(Math.random() * (maxValue - minValue)) + minValue;
    },

    checkResult() {
      let mode = "answer-error";

      if (this.response == this.result) {
        mode = "answer-success";
      }

      this.$emit("changeMode", mode);

      this.generateQuestion();
    }
  }
};
</script>

<style scoped></style>
