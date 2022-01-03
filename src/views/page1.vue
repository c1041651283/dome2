<template>
  <div>
    <h1>这是第一个画面</h1>
    <button @click="backIndex">回到主页</button>
  </div>
</template>

<script>
export default {
  name: "page1",
  methods: {
    backIndex() {
      this.$router.replace("/index");
    },
  },
};
</script>

<style scoped></style>
