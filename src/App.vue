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

    <BaseBeverage :color="color"/>
    <ul>
      <li>
        <template v-for="(base, index) in bases" :key="base">
          <label>
            <input
              @change="updateBaseColor"
              type="radio"
              name="base"
              :id="`r${base.id}`"
              :value="base.color"
              :checked="index === 0"
              v-model="baseColor"
            />
            {{ base.name }}
          </label>
          <baseBeverage :class="baseColor"/>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(cream, index) in creamers" :key="cream">
          <label>
            <input
              @change="updateCreamColor"
              type="radio"
              name="creamer"
              :id="`r${cream.id}`"
              :value="cream.color"
              :checked="index === 0"
              v-model="creamerColor"
            />
            {{ cream.name }}
          </label>
          <froth :class="creamColor"/>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <template v-for="(syrup, index) in syrups" :key="syrup">
          <label>
            <input
              @change="updateSyrupColor"
              type="radio"
              name="syrup"
              :id="`r${syrup.id}`"
              :value="syrup.color"
              :checked="index===0"
              v-model="syrupColor"
            />
            {{ syrup.name }}
          </label>
          <froth :class="syrupColor"/>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp } from "./stores/beverage";
import { bases, creamers, syrups } from "./stores/beverage";
import Base from "./components/Base.vue"
import Creamer from "./components/Creamer.vue"
import Syrup from "./components/Syrup.vue"

const baseColor = ref(bases[0]?.color || null);
const updateBaseColor = (event) => {
  baseColor.value = event.target.value
}

const creamColor = ref(null)
const updateCreamColor = (event) => {
  creamColor.value = event.target.value
}

const syrupColor = ref(null)
const updateSyrupColor = (event) => {
  syrupColor.value = event.target.value
}

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
