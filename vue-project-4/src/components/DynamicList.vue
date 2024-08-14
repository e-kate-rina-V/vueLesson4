<!--Створіть динамічний список елементів, де кожен елемент має випадковий колір фону та розмір шрифту, 
згенеровані методом при створенні компоненту.-->

<!--Реалізуйте динамічне змінення стилів елемента (наприклад, зміна позиції, коліру, розміру) 
за допомогою CSS Transitions або Animations при натисканні кнопки.-->

<template>
  <div class="dynamic-list">
    <button @click="changeStyles">Змінити стилі</button>
    <ul id="dynamic-ul">
      <li id="dynamic-li" v-for="(item, index) in items" :key="index" :style="item.style">
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: this.generateItems(),
    };
  },
  methods: {
    generateItems() {
      const colors = ['#FF5733', '#33FF57', '#3357FF', '#F0F0F0', '#000000'];
      const fontSizes = ['14px', '18px', '22px', '26px', '30px'];
      const items = [];

      for (let i = 0; i < 5; i++) {
        items.push({
          text: `Елемент ${i + 1}`,
          style: {
            backgroundColor: colors[Math.floor(Math.random() * colors.length)],
            fontSize: fontSizes[Math.floor(Math.random() * fontSizes.length)],
            padding: '10px',
            margin: '5px',
            borderRadius: '5px',
            color: '#ffffff',
            transition: 'all 0.5s ease'
          },
        });
      }
      return items;
    },
    changeStyles() {
      this.items = this.items.map(item => ({
        ...item,
        style: {
          ...item.style,
          backgroundColor: this.getRandomColor(),
          fontSize: this.getRandomFontSize(),
          transform: `translate(${Math.random() * 100}px, ${Math.random() * 100}px)`,
        },
      }));
    },
    getRandomColor() {
      const colors = ['#FF5733', '#33FF57', '#3357FF', '#F0F0F0', '#000000'];
      return colors[Math.floor(Math.random() * colors.length)];
    },
    getRandomFontSize() {
      const fontSizes = ['14px', '18px', '22px', '26px', '30px'];
      return fontSizes[Math.floor(Math.random() * fontSizes.length)];
    },
  },
};
</script>
