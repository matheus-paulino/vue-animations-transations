<template>
  <div class="alert alert-danger" role="alert">
    <h2 class="alert-heading" v-text="title"></h2>
    <hr />
    <p>Você errou o resultado da pergunta</p>
    <button class="btn btn-info btn-md rounded-0" @click.prevent="nextQuestion">
      Próxima pergunta
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Você errou"
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
.error {
  border: 2px solid red;
  padding: 30px;
}
</style>
