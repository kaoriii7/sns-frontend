<template>
  <header>
    <div class="logo">
      <img src="@/assets/logo.png" />
    </div>
    <ul>
      <li class="menu-item" v-if="!$auth.loggedIn">
        <NuxtLink to="/register">新規登録</NuxtLink>
      </li>
      <li class="menu-item" v-if="!$auth.loggedIn">
        <NuxtLink to="/login">ログイン</NuxtLink>
      </li>
    </ul>
  </header>
</template>

<script>

</script>

<style scoped>
* {
  box-sizing: border-box;
}

header {
  display: flex;
  justify-content: space-between;
  height: 150px;
  background: #001100;
}

.logo {
  width: 150px;
  margin: 20px;
}

img {
  width: 100%;
}

ul {
  display: flex;
}

li {
  list-style: none;
  margin: 30px 10px;
}

a {
    text-decoration: none;
    color: white;
}
</style>