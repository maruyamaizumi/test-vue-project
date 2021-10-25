<template>
  <h2>
    テストコンポーネント
  </h2>
  <p>
    {{ comment }}
  </p>
</template>

<script>
export default{
  name: 'TestComponent',
  props: {
    comment: String
  }
}
</script>

<style scoped>
h2{
  color: red;
}
</style>