<script setup>
import Grid from "../Grid.vue";
import { gymHealthFacts, workoutProgram } from "../../utils";
console.log(gymHealthFacts);
const props = defineProps({
  handleSelectedWorkout: Function,
  firstIncompleteWorkoutIndex: Number,
  handleResetPlan: Function,
});

// Pick a random health fact to display as the daily tip
const randomNumber = Math.floor(Math.random() / gymHealthFacts.length);
const todaysFact = gymHealthFacts[randomNumber];
</script>

<template>
  <section id="dashboard">
    <div class="card-tip-container">
      <h1>Welcome Soldier</h1>
    </div>
    <div>
      <div>
        <p class="tip">
          <strong>Daily tip</strong><br />
          {{ todaysFact }}
          <br />
        </p>
        <button
          @click="
            () =>
              handleSelectedWorkout(
                firstIncompleteWorkoutIndex < 0
                  ? 0
                  : firstIncompleteWorkoutIndex,
              )
          "
        >
          Start workout &rarr;
        </button>
      </div>
    </div>
    <Grid v-bind="props" />
  </section>
</template>

<style scoped>
.tip-container,
.tip-container div,
#dashboard {
  display: flex;
}

.tip-container,
#dashboard {
  flex-direction: column;
}

#dashboard {
  gap: 2rem;
}

.tip-container {
  gap: 0.5rem;
}

@media (min-width: 640px) {
  .tip-container {
    gap: 1rem;
  }
}
</style>
