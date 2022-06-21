<template>
  <div class="container">
    <form @submit.prevent="signup">
      <div class="content">
        <p class="register">Реєстрація</p>
        <div class="model-container">
          <p class="label">Ім'я</p>
          <input type="text" name="first_name" v-model="first_name" placeholder="..." />
        </div>
        <div class="model-container">
          <p class="label">Прізвище</p>
          <input type="text" name="last_name" v-model="last_name" placeholder="..." />
        </div>
        <div class="model-container">
          <p class="label">Пошта</p>
          <input type="text" name="email" v-model="email" placeholder="ivanko.ukraine@gmail.com" />
        </div>
        <div class="model-container">
          <p class="label">Пароль</p>
          <input type="text" name="password" v-model="password" placeholder="********" />
        </div>
        <div class="model-container">
          <p class="label">Роль</p>
          <select name="role" v-model="role">
            <option>client</option>
            <option>driver</option>
          </select>
        </div>
        <button>Зареєструватися</button>
      </div>
    </form>
  </div>
</template>

<style>
.container {
  display: flex;
  flex: 1;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.container:before:after {
  box-sizing: inherit;
}
form {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 100%;
}
p {
  margin: 0;
  font-family: 'Gilroy-Light';
}
.content {
  width: 56%;
  display: flex;
  flex-direction: column;
  padding: 40px 40px 25px 40px;
  box-sizing: border-box;
}
.register {
  font-size: 32px;
  line-height: 43.2px;
}
input {
  width: 100%;
  padding: 8px 16px;
  font-size: 16px;
  font-family: 'Gilroy-Light';
  border: 2px solid #9ca3af;
  border-radius: 8px;
  margin-top: 4px;
  color: #ffffff;
}
.model-container {
  margin-top: 12px;
}
.label {
  font-size: 16px;
  line-height: 24px;
}
.password {
  margin-top: 28px;
}
button {
  font-size: 24px;
  line-height: 43.2px;
  background: #e5e7eb;
  border: 4px solid #9ca3af;
  border-radius: 8px;
  margin-top: 35px;
  padding: 4px;
  color: #000000;
}
button:active {
  transform: scale(0.98);
  box-shadow: 3px 2px 3px 1px rgba(0, 0, 0, 0.24);
}
select {
  width: 100%;
  border: 2px solid #9ca3af;
  border-radius: 8px;
  padding: 8px 16px;
  font-size: 16px;
  color: #ffffff;
}
</style>

<script>
export default {
  name: 'App',
  data() {
    return {
      first_name: '',
      last_name: '',
      email: '',
      password: '',
      role: 'client',
    };
  },
  methods: {
    async login() {
      const { first_name, last_name, email, password, role } = this;
      const res = await fetch('http://localhost:3000/auth/signup', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          first_name,
          last_name,
          email,
          password,
          role,
        }),
      });
      const data = await res.json();
      console.log(data);
      if (res.ok) {
        this.$router.push('/');
      }
    },
  },
};
</script>
