<script>
export default {
  methods: {
    add() {
      this.$router.push('/add')
    }
  },
}
</script>
<template>
  <div class="add">
    <button @click="add" class="light icon-l">
      <fa-icon :icon="['fas', 'plus']" />
      Add article
    </button>
  </div>
</template>

<style lang="scss" scoped>
button {
  width: 100%;
}
</style>