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

// Returns true when all exercise weight inputs for the selected workout are filled in
const isWorkoutComplete = computed(() => {
  const currWorkout = data.value?.[selectedWorkout.value];
  if (!currWorkout) {
    return false;
  } // guard clause to exit function

  const isCompleteCheck = Object.values(currWorkout).every((ex) => !!ex);
  console.log("ISCOMPLETE: ", isCompleteCheck);
  return isCompleteCheck;
});

// Returns the index of the first workout that still has empty fields, or -1 if all are complete
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

// Switches the visible page (1=Welcome, 2=Dashboard, 3=Workout)
function handleChangeDisplay(idx) {
  selectedDisplay.value = idx;
}

// Navigates to the Workout page and sets the selected workout by index
function handleSelectedWorkout(idx) {
  selectedDisplay.value = 3;
  selectedWorkout.value = idx;
}

// Persists workout data to localStorage and redirects back to the Dashboard
function handleSaveWorkout() {
  localStorage.setItem("workouts", JSON.stringify(data.value));
  selectedDisplay.value = 2;
  selectedWorkout.value = -1;
}

// Clears all workout progress, removes saved data from localStorage, and returns to Dashboard
function handleResetPlan() {
  selectedDisplay.value = 2;
  selectedWorkout.value = -1;
  data.value = defaultData;
  localStorage.removeItem("workouts");
  console.log("reset");
}

// On mount, restores saved workout data from localStorage and skips the Welcome page
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
