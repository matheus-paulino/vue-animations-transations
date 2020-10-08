<template>
  <div class="alert alert-success" role="alert">
    <h2 v-text="title" class="alert-heading"></h2>
    <hr />
    <p>Resposta correta</p>

    <button class="btn btn-info btn-md rounded-0" @click.prevent="nextQuestion">
      Próxima pergunta
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Você acertou!"
    };
  },
  methods: {
    nextQuestion() {
      this.$emit("changeMode");
    }
  }
};
</script>

<style scoped>
.success {
  border: 2px solid greenyellow;
  padding: 30px;
}
</style>
