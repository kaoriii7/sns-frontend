<template>
  <header>
    <div class="logo">
      <img src="@/assets/logo.png" />
    </div>
    <ul>
      <li class="menu-item">
        <NuxtLink to="/"><img src="@/assets/home.png" />ホーム</NuxtLink>
      </li>
      <li class="menu-item">
        <a @click="logout"><img src="@/assets/logout.png" />ログアウト</a>
      </li>
    </ul>
    <form @submit.prevent="store">
      <label for="">シェア<textarea name="textarea" id="textarea" v-model="textarea" cols="30" rows="4" required></textarea></label>
      <button type="submit">シェアする</button>
    </form>
  </header>
</template>

<script>
export default {
  data() {
    return {
      textarea: '',
    };
  },
  methods: {
    async logout() {
      try {
        await this.$auth.logout();
        this.$router.push("/login");
      } catch(error) {
        console.log(error);
      }
    },
    async store() {
      await this.$axios.post("http://localhost:8000/api/auth/", {
          textarea: this.textarea,
        });
        this.$router.push("/");
    }
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

img {
  vertical-align: bottom;
}

header {
  background: #001100;
  width: 300px;
  padding: 10px;
}

.logo {
  width: 120px;
  margin-bottom: 20px;
}

.logo img {
  width: 100%;
}

.menu-item img {
  width: 25px;
  margin-right: 10px;
}

li {
  list-style: none;
  margin: 20px 10px;
}

a {
  text-decoration: none;
  color: white;
  cursor: pointer;
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