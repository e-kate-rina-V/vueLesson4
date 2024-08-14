<!--Реалізуйте компонент, що виводить список об'єктів, де кожен об'єкт має вкладений список. 
Використовуйте вкладені v-for для виведення елементів вкладеного списку.-->

<!--Виведіть список елементів, використовуючи v-for, і 
додайте умову v-if для фільтрації елементів.-->

<template>
  <div class="object-list">
    <label for="filter">Filter items: </label>
    <input id="filter" v-model="filterText" placeholder="Type to filter" />
    <ul id="object-ul">
      <li id="object-li" v-for="item in filteredItems" :key="item.id">
        {{ item.name }}
        <ul v-if="item.subItems && item.subItems.length" class="sub-list">
          <li v-for="subItem in item.subItems" :key="subItem.id">
            {{ subItem.name }}
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          id: 1,
          name: 'Fruits',
          subItems: [
            { id: 1.1, name: 'Apple' },
            { id: 1.2, name: 'Banana' }
          ]
        },
        {
          id: 2,
          name: 'Vegetables',
          subItems: [
            { id: 2.1, name: 'Carrot' },
            { id: 2.2, name: 'Broccoli' }
          ]
        },
      ],
      filterText: ''
    };
  },
  computed: {
    filteredItems() {
      const lowerCaseFilter = this.filterText.toLowerCase();
      return this.items.filter(item =>
        item.name.toLowerCase().includes(lowerCaseFilter)
      );
    }
  }
};
</script>
