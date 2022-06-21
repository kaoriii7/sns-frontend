<template>
  <div>
    <h1>ホーム</h1>
    <div>
    <p>ユーザーネーム: {{ $auth.user.name }}</p>
    <p>share</p>
    </div>
  </div>
</template>

<script>
export default {

  layout: 'homeDefault'
}
</script>

<style>

</style>