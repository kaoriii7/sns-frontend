<template>
  <div class="register">
    <div class="container">
      <h2>新規登録</h2>
      <form @submit.prevent="register">
        <input class="input" type="text" v-model="name" placeholder="ユーザーネーム" required />
        <input class="input" type="email" v-model="email" placeholder="メールアドレス" required />
        <input class="input" type="password" v-model="password" placeholder="パスワード" required />
        <button type="submit">新規登録</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  auth: false,
  dara() {
    return {
      name: null,
      email: null,
      password: null,
    };
  },
  methods: {
    async register() {
      try {
        await this.$axios.post("http://localhost:8000/api/auth/register", {
          name: this.name,
          email: this.email,
          password: this.password,
        });
        this.$router.push("/login");
      } catch {
        alert("メールアドレスがすでに登録されています");
      }
    },
  },
};
</script>

<style>
.register {
  display: flex;
  background: #001100;
  height: 100vh;
}

.container {
  background: #fff;
  width: 320px;
  height: 220px;
  padding: 30px;
  margin: 0 auto;
  text-align: center;
  border-radius: 3px;
}

.input {
  width: 270px;
  display: flex;
  flex-direction: column;
  margin: 15px auto;
  padding: 12px;
  border: 2px solid black;
  border-radius: 10px;
  font-size: 10px;
}

button {
  width: 100px;
  line-height: 35px;
  border-radius: 30px;
  color: #fff;
  background: #330099;
  border: 1px solid #330099;
  cursor: pointer;
}
</style>