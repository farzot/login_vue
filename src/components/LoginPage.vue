<!-- <template>
  <div class="login">
    <h2>Login Page</h2>
    <form @submit.prevent="login">
      <div>
        <label for="username">Username:</label>
        <input type="text" v-model="username" required />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" v-model="password" required />
      </div>
      <button type="submit">Login</button>
      <p v-if="errorMessage">{{ errorMessage }}</p>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'LoginPage',
  data() {
    return {
      username: '',
      password: '',
      errorMessage: ''
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.get('https://dummyjson.com/users');
        const users = response.data.users; // Foydalanuvchilar ro'yxati
        console.log(response.data.users);
        

        const user = users.find(
          (u) => u.username === this.username && u.password === this.password
        );
        console.log(user);
        
        if (user) {
          this.$router.push({ name: 'HomePage' });
        } else {
          this.errorMessage = 'Invalid username or password.';
        }
      } catch (error) {
        console.error(error);
        this.errorMessage = 'An error occurred while logging in.';
      }
    }
  }
};
</script>

<style scoped>
.login {
  max-width: 400px;
  margin: auto;
}
form div {
  margin-bottom: 10px;
}
</style> -->
<template>
  <div class="login-background">
    <div class="modal">
      <h2>Login Page</h2>
      <form @submit.prevent="login">
        <div class="form-group">
          <label for="username">Username:</label>
          <input type="text" v-model="username" required />
        </div>
        <div class="form-group">
          <label for="password">Password:</label>
          <input type="password" v-model="password" required />
        </div>
        <button type="submit">Login</button>
        <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'LoginPage',
  data() {
    return {
      username: '',
      password: '',
      errorMessage: ''
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.get('https://dummyjson.com/users');
        const users = response.data.users;

        const user = users.find(
          (u) => u.username === this.username && u.password === this.password
        );

        if (user) {
          this.$router.push({ name: 'HomePage' });
        } else {
          this.errorMessage = 'Invalid username or password.';
        }
      } catch (error) {
        console.error(error);
        this.errorMessage = 'An error occurred while logging in.';
      }
    }
  }
};
</script>

<style scoped>
.login-background {
  background-color: #f7e07a; /* Sariq fon rangi */
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: 'Arial', sans-serif; /* Shrift */
}

.modal {
  background-color: white; /* Modal fon rangi */
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  width: 350px; /* Modal kengligi */
  text-align: center; /* Matnni markazga joylashtirish */
}

h2 {
  margin-bottom: 20px; /* Sarlavha va formaning orasini bo'sh joy qiling */
}

.form-group {
  margin-bottom: 15px; /* Formaning elementlari orasidagi bo'sh joy */
}

label {
  display: block; /* Labelni blok holatiga o'tkazing */
  margin-bottom: 5px; /* Label va input orasida bo'sh joy */
}

input {
  width: 100%; /* Inputning kengligini 100% ga o'rnating */
  padding: 10px;
  border: 1px solid #ccc; /* Input uchun chegara rangi */
  border-radius: 5px; /* Inputning burchaklarini yumshatish */
  transition: border-color 0.3s; /* Chiziq rangi o'zgarishi */
}

input:focus {
  border-color: #ffcc00; /* Fokusda input chiziq rangi */
}

button {
  width: 100%; /* Tugmani kengligini 100% ga o'rnating */
  padding: 10px;
  background-color: #ffcc00; /* Tugma fon rangi */
  border: none; /* Chegarani olib tashlang */
  border-radius: 5px; /* Tugma burchaklarini yumshatish */
  color: white; /* Matn rangini oq rangga o'rnating */
  font-size: 16px; /* Matn o'lchami */
  cursor: pointer; /* Kursor ko'rsatgichini qo'shing */
}

button:hover {
  background-color: #e6b800; /* Tugma ustiga kelsa rang o'zgarishi */
}

.error-message {
  color: red; /* Xato xabari rangi */
  margin-top: 10px; /* Xato xabari va tugma orasida bo'sh joy */
}
</style>
