<template>
  <div class="layout__main">
    <!-- Vertical navigation menu -->
    <div
      class="vertical-nav-menu"
      :class="{ 'close': isCloseMenu }">
      <vertical-nav-menu
      @toggle-menu="isCloseMenu = !isCloseMenu"
      :is-close-menu="isCloseMenu"/>
    </div>

    <!-- Content -->
    <div
      class="layout__main__container"
      :class="{ 'close': isCloseMenu }">
      <!-- Nav bar -->
      <nav-bar />

      <!-- Breadcrump -->
      <breadcrump />

      <!-- Dianmic content -->
      <div class="container__inner w-full">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {
    navBar: () => import('@/components/navBar/Index.vue'),
    breadcrump: () => import('@/components/Breadcrump.vue'),
    verticalNavMenu: () => import('@/components/verticalNavMenu/Index.vue')
  },
  data () {
    return {
      isCloseMenu: true
    }
  }
}
</script>

<style lang="scss" scoped>
.layout__main {
  width: 100%;

  .vertical-nav-menu {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 10000;
    width: $menu-opened;
    height: 100%;
    border-radius: 0;
    background-color: $dark;
    transition: 0.4s;
    overflow: hidden;

    &.close {
      width: $menu-closed;
    }
  }
  .layout__main__container {
    width: calc(100% - #{$menu-opened});
    min-height: 100vh;
    height: 100%;
    margin-left: $menu-opened;
    padding: 25px 86px;
    background-color: #F5F5F6;
    transition: 0.4s;

    &.close {
      width: calc(100% - #{$menu-closed});
      margin-left: $menu-closed;
    }
  }
}
</style>
