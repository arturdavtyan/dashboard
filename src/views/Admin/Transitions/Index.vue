<template>
  <div class="container-view">
    <div class="header flex items-center justify-between">
      <span class="section-name">UI/UX Designer</span>
      <div class="navs flex items-center">
        <router-link to="#">OVERVIEW</router-link>
        <router-link to="#">ACTIVITY LOG</router-link>
        <router-link to="#">MEMBERS</router-link>
        <router-link to="#">ACCESSES</router-link>
        <router-link to="#">TASKS</router-link>
        <router-link to="#">ASSETS</router-link>
        <router-link to="#" class="active">MEETINGS</router-link>
      </div>
    </div>

    <router-view />
  </div>
</template>

<style lang="scss" scoped>
.header {
  margin-bottom: 2.358rem;

  .section-name {
    font-size: 4rem;
    letter-spacing: 0px;
    font-weight: bold;
  }
  .navs {
    height: 82px;
    padding: 0 22px;
    border-radius: 60px;
    background-color: #fff;

    a {
      margin: 0 8px;
      padding: 8px 14px;
      border-radius: 60px;

      &.active {
        background-color: $dark-primary;
        color: #fff;
      }
    }
  }
}
</style>
