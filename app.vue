<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choose a gender</h4>
        <div class="option-buttons">
          <button
            class="option option-left"
            :class="options.gender === Gender.BOY && 'active'"
            @click="options.gender = Gender.BOY"
          >
            Boy
          </button>
          <button
            class="option"
            :class="options.gender === Gender.UNISEX && 'active'"
            @click="options.gender = Gender.UNISEX"
          >
            Unisex
          </button>
          <button
            class="option option-right"
            :class="options.gender === Gender.GIRL && 'active'"
            @click="options.gender = Gender.GIRL"
          >
            Girl
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose the name's popularity</h4>
        <div class="option-buttons">
          <button
            class="option option-left"
            :class="options.popularity === Popularity.TRENDY && 'active'" 
            @click="options.popularity = Popularity.TRENDY"
          >
            Trendy
          </button>
          <button
            class="option option-right"
            :class="options.popularity === Popularity.UNIQUE && 'active'"
            @click="options.popularity = Popularity.UNIQUE"
          >
            Unique
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choose name's length</h4>
        <div class="option-buttons">
          <button
            class="option option-left"
            :class="options.length === Length.LONG && 'active'"
            @click="options.length = Length.LONG"
          >
            Long
          </button>
          <button class="option" 
          :class="options.length === Length.ALL && 'active'"
          @click="options.length = Length.ALL"
          >
            All
          </button>
          <button
            class="option option-right"
            :class="options.length === Length.SHORT && 'active'"
            @click="options.length = Length.SHORT"
          >
            Short
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">

enum Gender {
  GIRL = "Girl",
  BOY = "Boy",
  UNISEX = "Unisex"
}
enum Popularity {
  UNIQUE = "Unique",
  TRENDY = "Trendy",
}
enum Length {
  LONG = "Long",
  SHORT = "Short",
  ALL = "All"
}

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

// Test object
// const obj: OptionsState = {
//   gender: Gender.BOY,
//   popularity: Popularity.TRENDY,
//   length: Length.LONG,
// };


// First way to use OptionsState
// const options = reactive<OptionsState>({
//   gender: Gender.BOY,
//   popularity: Popularity.TRENDY,
//   length: Length.LONG,
// });

// Second way to use OptionsState
const options: OptionsState = reactive({
  gender: Gender.BOY,
  popularity: Popularity.UNIQUE,
  length: Length.LONG,
});
</script>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}
h1 {
  font-size: 3rem;
}
.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}
.option-container {
  margin-bottom: 2rem;
}

.option {
  background: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}

.option-left {
  border-radius: 1rem 0 0 1rem;
}
.option-right {
  border-radius: 0 1rem 1rem 0;
}

.active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>
