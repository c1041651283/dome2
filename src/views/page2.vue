<template>
  <div>
    <h2>这是第二个画面</h2>
    <button @click="backIndex">回到主页</button>
  </div>
</template>

<script>
export default {
  name: "page2",
  methods: {
    backIndex() {
      this.$router.replace("/index");
    },
  },
};
</script>

<style scoped></style>
