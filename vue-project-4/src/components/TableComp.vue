<!--За допомогою v-for, створіть таблицю, де кількість рядків і 
стовпців задається динамічно через інпут або інший елемент керування.-->

<!--Створіть переключатель тем, який динамічно змінює стилі всього додатку 
між темною та світлою темами.-->

<template>
  <div class="table" :class="theme">
    <button id="toggle-theme-btn" @click="toggleTheme">
      Toggle Theme (Current: {{ theme }})
    </button>

    <label for="rows">Rows:</label>
    <input id="rows" type="number" v-model.number="rows" min="1" />

    <label for="cols">Columns:</label>
    <input id="cols" type="number" v-model.number="cols" min="1" />

    <table>
      <tbody>
        <tr v-for="row in rows" :key="'row-' + row">
          <td v-for="col in cols" :key="'col-' + col">
            {{ row }}-{{ col }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rows: 1,
      cols: 1,
      theme: 'light'
    };
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
    }
  }
};
</script>
