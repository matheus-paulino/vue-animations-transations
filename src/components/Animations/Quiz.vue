<template>
  <div class="container">
    <h2>{{ title }}</h2>

    <div class="row">
      <div class="col-md-12">
        <transition name="effect" mode="out-in">
          <component :is="mode" @changeMode="changeMode"></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Question from "./Question";
import AnswerSuccess from "./AnswerSuccess";
import AnswerError from "./AnswerError";

export default {
  data() {
    return {
      title: "Quiz",
      mode: "app-question"
    };
  },

  components: {
    "app-question": Question,
    AnswerSuccess,
    AnswerError
  },
  methods: {
    changeMode(mode) {
      if (mode == undefined) this.mode = "app-question";
      else this.mode = mode;
    }
  }
};
</script>

<style scoped>
.effect-leave-active {
  animation: effect-out 1s;
}

.effect-enter-active {
  animation: effect-in 1s;
}

@keyframes effect-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(90deg);
  }
}

@keyframes effect-in {
  from {
    transform: rotateY(90deg);
  }

  to {
    transform: rotateY(0deg);
  }
}
</style>
