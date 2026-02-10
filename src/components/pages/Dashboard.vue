<script setup>
import { gymHealthFacts } from "../../utils";
console.log(gymHealthFacts);
// Generate a random integer
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
        <button>Start workout &rarr;</button>
      </div>
    </div>
  </section>
</template>

<style scoped></style>
