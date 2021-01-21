<template>
  <div class="primary-dark-button">
    <button @click="$router.push(to).catch(() => {})"><slot /></button>
  </div>
</template>

<script>
export default {
  name: 'primary-dark-button',
  props: ['to']
}
</script>

<style lang="scss" scoped>
.primary-dark-button {
  width: 100%;
  height: 51px;
  border-radius: 10px;
  overflow: hidden;

  button {
    width: 100%;
    min-width: 120px;
    height: 100%;
    padding: 0 12px;
    border: none;
    font-size: 1rem;
    background-color: $dark-primary;
    color: #fff;
    cursor: pointer;
  }
}
</style>
