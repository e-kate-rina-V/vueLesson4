<!--Створіть компонент, де кожен клік на кнопку зберігає поточний час кліка 
в масив і виводить цей масив на екран.-->

<template>
  <div class="save-time">
    <button @click="logTime" id="save-time-btn">Зберегти час</button>
    <p>Часи кліків:</p>
    <p v-if="clickTimes.length === 0">Поки немає кліків</p>
    <ul id="save-time-ul">
      <li id="save-time-li" v-for="(time, index) in clickTimes" :key="index">{{ time }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clickTimes: [],
    };
  },
  methods: {
    logTime() {
      const currentTime = new Date().toLocaleTimeString();
      this.clickTimes.push(currentTime);
    },
  },
};
</script>
