<script setup>
import Layout from "./components/layouts/Layout.vue";
import Welcome from "./components/pages/Welcome.vue";
import Dashboard from "./components/pages/Dashboard.vue";
import Workout from "./components/pages/Workout.vue";
import { ref, computed, onMounted } from "vue";
import { workoutProgram } from "./utils";

const defaultData = {};
for (let workoutIdx in workoutProgram) {
  const workoutData = workoutProgram[workoutIdx];
  defaultData[workoutIdx] = {};

  for (let e of workoutData.workout) {
    defaultData[workoutIdx][e.name] = "";
  }
}

const selectedDisplay = ref(1);
const data = ref(defaultData);
const selectedWorkout = ref(-1);

const isWorkoutComplete = computed(() => {
  const currWorkout = data.value?.[selectedWorkout.value];
  if (!currWorkout) {
    return false;
  } // guard clause to exit function

  const isCompleteCheck = Object.values(currWorkout).every((ex) => !!ex);
  console.log("ISCOMPLETE: ", isCompleteCheck);
  return isCompleteCheck;
});

const firstIncompleteWorkoutIndex = computed(() => {
  const allWorkouts = data.value;
  if (!allWorkouts) {
    return -1;
  }

  // loop over every key value pair, and check if the workout is complete or not
  for (const [index, workout] of Object.entries(allWorkouts)) {
    const isComplete = Object.values(workout).every((ex) => !!ex);
    if (!isComplete) {
      return parseInt(index);
    }
  }
  return -1; // all are complete
});

function handleChangeDisplay(idx) {
  selectedDisplay.value = idx;
}

function handleSelectedWorkout(idx) {
  selectedDisplay.value = 3;
  selectedWorkout.value = idx;
}

function handleSaveWorkout() {
  localStorage.setItem("workouts", JSON.stringify(data.value));
  selectedDisplay.value = 2;
  selectedWorkout.value = -1;
}

function handleResetPlan() {
  selectedDisplay.value = 2;
  selectedWorkout.value = -1;
  data.value = defaultData;
  localStorage.removeItem("workouts");
  console.log("reset");
}

onMounted(() => {
  console.log("Page Mounted");
  if (!localStorage) {
    return;
  }
  if (localStorage.getItem("workouts")) {
    const savedData = JSON.parse(localStorage.getItem("workouts"));
    data.value = savedData;
    selectedDisplay.value = 2; //avoid always landing in the welcome screen
  }
});
</script>

<template>
  <Layout>
    <!-- PAGE 1 -->
    <Welcome
      :handleChangeDisplay="handleChangeDisplay"
      v-if="selectedDisplay == 1"
    />
    <!-- PAGE 2 -->
    <Dashboard
      :firstIncompleteWorkoutIndex="firstIncompleteWorkoutIndex"
      :handleSelectedWorkout="handleSelectedWorkout"
      :handleResetPlan="handleResetPlan"
      v-if="selectedDisplay == 2"
    />
    <!-- PAGE 3 -->
    <Workout
      :data="data"
      :selectedWorkout="selectedWorkout"
      :isWorkoutComplete="isWorkoutComplete"
      :handleSaveWorkout="handleSaveWorkout"
      v-if="workoutProgram?.[selectedWorkout]"
    />
  </Layout>
</template>

<style scoped></style>
