<template>
  <div class="container">
    <form @submit.prevent="login">
      <div class="content">
        <p class="login">Логін</p>
        <div class="email">
          <p class="label">Email</p>
          <input type="text" name="email" v-model='email' placeholder="ivanko.ukraine@gmail.com" />
        </div>
        <div class="password">
          <p class="label">Пароль</p>
          <input type="text" name="password" v-model="password" placeholder="********" />
        </div>
        <button>Увійти</button>
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
.login {
  font-size: 36px;
  line-height: 43.2px;
}
input {
  width: 100%;
  padding: 12px;
  font-size: 20px;
  font-family: 'Gilroy-Light';
  border: 2px solid #9ca3af;
  border-radius: 8px;
  margin-top: 4px;
  color: #ffffff;
}
.email {
  margin-top: 12px;
}
.label {
  font-size: 20px;
  line-height: 24px;
}
.password {
  margin-top: 28px;
}
button {
  font-size: 36px;
  line-height: 43.2px;
  background: #e5e7eb;
  border: 4px solid #9ca3af;
  border-radius: 8px;
  margin-top: 35px;
  padding: 12px;
  color: #000000;
}
button:active {
  transform: scale(0.98);
  box-shadow: 3px 2px 3px 1px rgba(0, 0, 0, 0.24);
}
</style>

<script>
export default {
  name: 'App',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  methods: {
    async login() {
      const { email, password } = this;
      const res = await fetch('http://localhost:3000/auth/login', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          email,
          password,
        }),
      });
      const data = await res.json();
      console.log(data);
    },
  },
};
</script>
