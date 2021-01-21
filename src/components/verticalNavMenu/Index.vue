<template>
  <div class="v-nav-menu">
    <!-- Logo -->
    <div class="v-nav-menu__logo flex items-center">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        viewBox="0 0 49.521 38.497"
        @click="$emit('toggle-menu')">
        <defs>
          <clipPath id="a">
            <rect class="a" width="49.521" height="38.497"/>
          </clipPath>
        </defs>
        <g class="b"><path class="c" d="M51.275,15.306,76.722.615a4.535,4.535,0,0,1,6.8,3.927V33.925a4.535,4.535,0,0,1-6.8,3.927L51.275,23.161a4.535,4.535,0,0,1,0-7.855" transform="translate(-34.003 0)"/><path class="d" d="M32.248,15.405,6.8.714A4.535,4.535,0,0,0,0,4.641V34.024a4.535,4.535,0,0,0,6.8,3.927L32.248,23.26a4.535,4.535,0,0,0,0-7.855" transform="translate(0.001 -0.069)"/><path class="e" d="M51.275,48.084l7.515,4.339,7.462-4.308a4.535,4.535,0,0,0,0-7.855l-7.515-4.339-7.462,4.308a4.535,4.535,0,0,0,0,7.855" transform="translate(-34.003 -24.923)"/>
        </g>
      </svg>
      <span
        class="v-nav-menu__logo-text"
        :class="{ 'closed': isCloseMenu }">TransitPru</span>
    </div>

    <!-- Menu -->
    <v-nav-menu :is-close-menu="isCloseMenu" />

    <!-- New -->
    <div class="v-nav-menu__new flex items-center ">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 54 54">
        <defs>
        </defs>
        <g transform="translate(0.447)">
          <circle class="a" cx="27" cy="27" r="27" transform="translate(-0.447)"/>
          <path class="b" d="M132.07-712.6q0,2.253,0,4.506a3.787,3.787,0,0,1-.04.622,1.023,1.023,0,0,1-1.047.9,1.01,1.01,0,0,1-.992-.91,6.448,6.448,0,0,1-.049-.889q-.005-4.439,0-8.878c0-.693-.031-.723-.737-.723q-4.506,0-9.011,0a3.864,3.864,0,0,1-.71-.045,1.008,1.008,0,0,1-.827-1.019,1.007,1.007,0,0,1,.809-.99,5.121,5.121,0,0,1,.932-.066q4.394-.007,8.788,0c.731,0,.756-.025.756-.749q0-4.394,0-8.788a5.464,5.464,0,0,1,.056-.888,1,1,0,0,1,1.03-.863.99.99,0,0,1,.989.856,4.715,4.715,0,0,1,.052.8q.005,4.461,0,8.922c0,.679.032.711.7.711q4.417,0,8.833,0a5.853,5.853,0,0,1,.889.054.99.99,0,0,1,.868,1.023.992.992,0,0,1-.886,1.009,4.834,4.834,0,0,1-.712.034q-4.483,0-8.967,0c-.7,0-.725.025-.726.73Q132.068-714.923,132.07-712.6Z" transform="translate(-104.253 745.665)"/>
      </g>
      </svg>
      <span
        class="v-nav-menu__logo-text"
        :class="{ 'closed': isCloseMenu }">New transition</span>
    </div>

  </div>
</template>

<script>
export default {
  name: 'vertical-nav-menu',
  props: ['isCloseMenu'],
  components: {
    vNavMenu: () => import('./verticalNavMenuItems')
  }
}
</script>

<style lang="scss" scoped>
.v-nav-menu {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: $menu-opened;
  min-height: 100%;
  padding: 39px 0 32px 21px;

  .v-nav-menu__logo {
    margin-left: 1px;

    .a{fill:none;}.b{clip-path:url(#a);}.c{fill:#43bccd;}.d{fill:#6d32a5;}.e{fill:#1d2585;}
    svg {
      width: 49.521px;
      height: 38.497px;
      cursor: pointer;
    }
    .v-nav-menu__logo-text {
      margin-left: 20.68px;
      font-weight: bold;
      font-size: 21px;
      color: #fff;
      transition: 0.5s;

      &.closed {
        opacity: 0;
      }
    }
  }
  .v-nav-menu__new {

    .a{fill:#6d32a5;}.b{fill:#fff;}
    svg {
      width: 54px;
      height: 54px;
      cursor: pointer;
    }
    .v-nav-menu__logo-text {
      margin-left: 20.68px;
      font-weight: bold;
      font-size: 1rem;
      color: #fff;
    }
  }
}
</style>
