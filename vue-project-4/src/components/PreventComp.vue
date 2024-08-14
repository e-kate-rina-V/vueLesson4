<!--Реалізуйте форму, де при submit ви використовуєте модіфікатор .prevent, і дані форми 
обробляються методом Vue інстанса, який також валідує їх на правильність введення перед відправкою.-->

<template>
  <div class="submit">
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="name">Ім'я: </label>
        <input type="text" v-model="name" id="name" />
        <span v-if="errors.name" class="error">{{ errors.name }}</span>
      </div>

      <div>
        <label for="email">Email: </label>
        <input type="email" v-model="email" id="email" />
        <span v-if="errors.email" class="error">{{ errors.email }}</span>
      </div>

      <button type="submit" id="submit-btn">Відправити</button>
    </form>

    <div v-if="submitted">
      <p>Форма успішно відправлена з наступними даними:</p>
      <p><strong>Ім'я:</strong> {{ name }}</p>
      <p><strong>Email:</strong> {{ email }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      errors: {},
      submitted: false,
    };
  },
  methods: {
    validateForm() {
      const errors = {};

      if (!this.name) {
        errors.name = "Ім'я обов'язкове";
      }

      if (!this.email) {
        errors.email = "Email обов'язковий";
      } else if (!/\S+@\S+\.\S+/.test(this.email)) {
        errors.email = "Невірний формат email";
      }

      this.errors = errors;
      return Object.keys(errors).length === 0;
    },
    handleSubmit() {
      if (this.validateForm()) {
        this.submitted = true;
        console.log('Форма відправлена з даними:', { name: this.name, email: this.email });
      }
    },
  },
};
</script>