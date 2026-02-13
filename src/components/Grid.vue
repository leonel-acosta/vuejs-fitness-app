<script setup>
import { workoutProgram } from "../utils";

const props = defineProps({
  handleSelectedWorkout: Function,
  firstIncompleteWorkoutIndex: Number,
  handleResetPlan: Function,
});

const workoutTypes = ["push", "Pull", "Legs"];
</script>

<template>
  <section id="grid">
    <button
      :disabled="workoutIdx > 0 && workoutIdx > firstIncompleteWorkoutIndex"
      @click="() => handleSelectedWorkout(workoutIdx)"
      :key="workoutIdx"
      v-for="(workout, workoutIdx) in Object.keys(workoutProgram)"
      class="card-button plan-card"
    >
      <div>
        <p>
          Day {{ workoutIdx < 9 ? "0" + (workoutIdx + 1) : workoutIdx + 1 }}
        </p>
        <i class="fa-solid fa-dumbbel" v-if="workoutIdx % 3 == 0"></i>
        <i class="fa-solid fa-weight-hanging" v-if="workoutIdx % 3 == 1"></i>
        <i class="fa-solid fa-boil" v-if="workoutIdx % 3 == 2"></i>
      </div>
      <h3>{{ workoutTypes[workoutIdx % 3] }}</h3>
    </button>
    <button
      :disabled="firstIncompleteWorkoutIndex != -1"
      @click="handleResetPlan"
    >
      Reset <i class="fa-solid fa-arrows-rotate"></i>
    </button>
  </section>
</template>

<style scoped>
#grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1em;
}
#grid button {
  width: 100%;
}

#grid button:disabled {
  box-shadow: none;
  cursor: not-allowed;
}

.plan-card {
  display: flex;
  flex-direction: column;
}

.plan-card div {
  display: flex;
  align-items: cemter;
  justify-content: space-between;
  gap: 0.5rem;
}

#plan-card div p {
  text-align: left;
}

@media (min-width: 640px) {
  #grid {
    grid-template-columns: repeat(4, minmax(0, 1fr));
  }
}
</style>
