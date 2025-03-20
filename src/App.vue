<template>
  <div>
    <Beverage :isIced="currentTemp === 'Cold'" />
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(base, index) in bases" :key="base.id">
          <label>
            <input
              type="radio"
              name="baseBeverage"
              :id="`r${base.id}`"
              :value="base"
              :checked="index === 0"
              v-model="currentBase"
            />
            {{ base.name }}
          </label>
        </template>
      </li>
    </ul>
    <BaseBeverage :color="currentBase.color" />

    <ul>
      <li>
        <template v-for="(cream, index) in creamers" :key="cream.id">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="`r${cream.id}`"
              :value="cream"
              :checked="index === 0"
              v-model="currentCream"
            />
            {{ cream.name }}
          </label>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(syrup, index) in syrups" :key="syrup.id">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="`r${syrup.id}`"
              :value="syrup"
              :checked="index===0"
              v-model="currentSyrup"
            />
            {{ syrup.name }}
          </label>
        </template>
      </li>
    </ul>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Beverage from "./components/Beverage.vue";
import { currentTemp, currentBase, currentCream, currentSyrup } from "./stores/beverage";
import { temps, bases, creamers, syrups } from "./stores/beverage";
import Base from "./components/Base.vue"
import Creamer from "./components/Creamer.vue"
import Syrup from "./components/Syrup.vue"

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
