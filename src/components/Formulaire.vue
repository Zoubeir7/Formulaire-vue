<template>
  <div class="form-container">
    <h1>Formulaire</h1>
    <form @submit.prevent="validateForm">
      <div class="form-group">
        <label for="name">Nom:</label>
        <input type="text" id="name" v-model="name" />
        <span v-if="errors.name" class="error">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" />
        <span v-if="errors.email" class="error">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label for="phone">Numéro de Téléphone:</label>
        <input type="tel" id="phone" v-model="phone" />
        <span v-if="errors.phone" class="error">{{ errors.phone }}</span>
      </div>

      <button type="submit">Soumettre</button>
      <p v-if="successMessage" class="success">{{ successMessage }}</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      errors: {},
      successMessage: ''
    };
  },
  methods: {
    validateForm() {
      this.errors = {};
      this.successMessage = '';

      if (!this.name) {
        this.errors.name = 'Le nom est requis.';
      }

      if (!this.email) {
        this.errors.email = 'L\'email est requis.';
      } else if (!this.isValidEmail(this.email)) {
        this.errors.email = 'L\'email n\'est pas valide.';
      }

      if (!this.phone) {
        this.errors.phone = 'Le numéro de téléphone est requis.';
      } else if (!this.isValidPhone(this.phone)) {
        this.errors.phone = 'Le numéro de téléphone n\'est pas valide.';
      }

      if (Object.keys(this.errors).length === 0) {
        this.successMessage = 'Formulaire soumis avec succès !';
        this.clearForm();
      }
    },
    isValidEmail(email) {
      const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return re.test(email);
    },
    isValidPhone(phone) {
      const re = /^\d{4}$/;
      return re.test(phone);
    },
    clearForm() {
      this.name = '';
      this.email = '';
      this.phone = '';
    }
  }
};
</script>

<style scoped>

.form-container {
  background-color: #ffffff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 50px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  width: 500px;
  margin: auto;

}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  color: #333;
}

input[type="text"],
input[type="email"],
input[type="tel"] {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: green;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: darkgreen;
}

.error {
  color: red;
  font-size: 12px;
  margin-top: 5px;
}

.success {
  color: green;
  font-size: 14px;
  text-align: center;
  margin-top: 20px;
}
</style>
