<template>
  <div class="target" @click="shot">
    <h1>CLICK ME</h1>
  </div>
</template>

<script>
export default {
  name: "Game",
  methods: {
    shot() {
      this.$emit("shot")
    }
  }
}
</script>

<style lang="css" scoped>

.target {
  background: #42b983;
  width: 200px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  margin: 0 auto;
}


h1 {
  color: #fff;
}

</style>