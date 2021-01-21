<template>
  <div
    class="v-nav-menu-item w-100 mt-3 mb-3 pt-4 pb-4 pl-8 flex items-center"
    :class="{'active': isActive}"
    @click="ChangeRoute(item)" >
    <div class="icon">
      <feather-icon :icon="item.icon" :svgClasses="isActive ? 'active' : 'menu-item'"></feather-icon>
    </div>
    <span v-if="!isClose" class="link-name ml-7">{{ item.name }}</span>
  </div>
</template>

<script>
export default {
  props: ['item', 'isClose', 'isShowMobileMenu'],
  computed: {
    isActive () {
      return this.$route.fullPath.includes(this.item.url)
    }
  },
  methods: {
    ChangeRoute (item) {
      this.isShowMobileMenu ? this.$eventHub.$emit('toggle-v-menu', false) : null
      this.$router.push(item.url).catch(() => {})
    }
  }
}
</script>

<style lang="scss" scoped>
.v-nav-menu-item {
  border-top-right-radius: 8px;
  border-bottom-right-radius: 8px;
  cursor: pointer;

  .icon {
    flex-basis: 26px;
    height: 26px;
    border-radius: 50%;
    // background-color: #eaeaea;
  }
  .link-name {
    font-size: 17px;
    color: $grey;
  }
  &:hover {
    background-color: #f1f1f1;
  }
  &.active {
    background: linear-gradient(90deg, $primary, $primary+b0);
    box-shadow: 0 0 8px 0px $primary;

    .link-name {
      color: $white;
    }
    .active {
      stroke: $white
    }
  }
}
</style>
