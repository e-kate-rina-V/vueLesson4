<!--Створіть два методи і динамічно змінюйте обробник події кліка між цими методами на основі деякої умови (наприклад, значення змінної).-->

<template>
  <div class="click">
    <button @click="handleClick" id="click-me-btn">Натисни мене</button>
    <p>Поточний метод: {{ currentMethod }}</p>
    <button @click="toggleMethod">Змінити метод</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      useMethodOne: true,
    };
  },
  computed: {
    currentMethod() {
      return this.useMethodOne ? 'Метод один' : 'Метод два';
    },
  },
  methods: {
    methodOne() {
      alert('Виконано метод один');
    },
    methodTwo() {
      alert('Виконано метод два');
    },
    handleClick() {
      if (this.useMethodOne) {
        this.methodOne();
      } else {
        this.methodTwo();
      }
    },
    toggleMethod() {
      this.useMethodOne = !this.useMethodOne;
    },
  },
};
</script>
