<!--Виведіть довгий список елементів з пагінацією, використовуючи v-for, 
і динамічно змінюйте відображені елементи при кліку на кнопки пагінації.-->

<template>
  <div class="pagin-list">
    <ul id="pagin-ul">
      <li id="pagin-li" v-for="item in paginatedItems" :key="item.id">
        {{ item.name }}
      </li>
    </ul>

    <div class="pagination">
      <button class="switch-page" @click="prevPage" :disabled="currentPage === 1">Previous</button>
      <span>Page {{ currentPage }} of {{ totalPages }}</span>
      <button class="switch-page" @click="nextPage" :disabled="currentPage === totalPages">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: Array.from({ length: 100 }, (_, i) => ({
        id: i + 1,
        name: `Item ${i + 1}`
      })),
      itemsPerPage: 10,
      currentPage: 1
    };
  },
  computed: {
    totalPages() {
      return Math.ceil(this.items.length / this.itemsPerPage);
    },
    paginatedItems() {
      const start = (this.currentPage - 1) * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return this.items.slice(start, end);
    }
  },
  methods: {
    prevPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
    nextPage() {
      if (this.currentPage < this.totalPages) {
        this.currentPage++;
      }
    }
  }
};
</script>
