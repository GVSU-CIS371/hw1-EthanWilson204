<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'" />
    <ul>
      <li>
        <template v-for="(temp, index) in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              :checked="index === 0"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(base, index) in bases" :key="base">
          <label>
            <input
              type="radio"
              name="base"
              :id="`r${base.id}`"
              :value="base.id"
              :checked="index === 0"
              v-model="baseOption"
            />
            {{ base.name }}
          </label>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(cream, index) in creamers" :key="cream">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`r${cream.id}`"
              :value="cream.id"
              :checked="index === 0"
              v-model="creamerOption"
            />
            {{ cream.name }}
          </label>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(syrup, index) in syrups" :key="syrup">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`r${syrup.id}`"
              :value="syrup.id"
              :checked="index===0"
              v-model="syrupOption"
            />
            {{ syrup.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>






</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp, bases, syrups, creamers } from "./stores/beverage";

</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
