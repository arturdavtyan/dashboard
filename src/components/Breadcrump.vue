<template>
  <div class="breadcrump flex items-center justify-start">
    <!-- <span>My Transitions</span>
    <img class="divider" :src="divider" alt="divider"> -->
    <!-- <span class="active">UI/UX Designer</span> -->

    <template
      v-for="(item, index) in breadcrumpList">
      <span
        v-if="item.active"
        class="active"
        :key="`route-${index}`">{{ item.title }}</span>
      <router-link
        v-else
        tag="span"
        class="flex items-center"
        :key="`route-${index}`"
        :to="item.url">{{ item.title }}<img class="divider" :src="divider" alt="divider"></router-link>
    </template>
  </div>
</template>

<script>
import dividerSvg from '@/assets/svgs/chevron-thin-down.svg'

export default {
  computed: {
    divider () {
      return dividerSvg
    },
    breadcrumpList () {
      return this.$route.meta.breadcrump
    }
  }
}
</script>

<style lang="scss" scoped>
.breadcrump {
  height: 21px;

  span {
    text-transform: uppercase;
    color: $primary;

    &:not(.active) {
      text-decoration: underline;
    }
  }
  .divider {
    margin: 0 0.67rem;
  }
}
</style>
