<template>
  <div class="primary-button">
    <button
      :disabled="disabled === true"
      @click="$router.push(to).catch(() => {})"><slot /></button>
  </div>
</template>

<script>
export default {
  name: 'primary-button',
  props: ['to', 'disabled']
}
</script>

<style lang="scss" scoped>
.primary-button {
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
    background-color: $primary;
    color: #fff;
    cursor: pointer;

    &:disabled {
      background-color: #A3A6B97d;
    }
  }
}
</style>
