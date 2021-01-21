<!-- ====================================================================
  Props: header [Array] (required)
         body [Array] (optional)
==================================================================== -->

<template>
  <table class="v-table">
    <thead class="v-table__head">
      <tr class="v-table__row">
        <td
          v-for="(elem, index) in header"
          :key="`v-table__cell-${index}`"
          :style="elem.fixed === true ? { 'width': `${elem.width}px` } : { 'min-width': `${elem.width}px` }"
          class="v-table__cell"
        >{{ elem.name }}</td>
      </tr>
      <!-- <tr class="v-table__row">
        <td
          v-for="(elem, index) in header"
          :key="`v-table__cell-${index}`"
          :style="{ 'min-width': `${elem.width}px` }"
          class="v-table__cell"
        >
          <div class="table__filter">
            <input
              type="text"
              class="filter__input"
            />
            <svg
              viewBox="0 0 459 459"
              class="filter__icon"
            >
              <g>
                <g>
                  <path d="M178.5,382.5h102v-51h-102V382.5z M0,76.5v51h459v-51H0z M76.5,255h306v-51h-306V255z"/>
                </g>
              </g>
              </svg>
          </div>
        </td>
      </tr> -->
    </thead>
    <tbody class="v-table__body">
      <slot />
    </tbody>
  </table>
</template>

<script>
// import DataNotFound from '@/components/DataNotFound.vue'

export default {
  name: 'v-table',
  components: {
    // DataNotFound,
    // PerPage
  },
  props: {
    header: {
      type: Array,
      default: () => []
    },
    body: {
      type: Array,
      default: () => []
    },
    listLength: {
      type: Number,
      default: 0
    },
    total: {
      type: Number,
      default: 0
    }
  },
  computed: {
    // currentPage: {
    //   get() {
    //     const page = Number(this.$route.query['page']) + 1
    //     return page || 1
    //   },
    //   set(value) {
    //     const per_page = this.$route.query['per-page']
    //     const query = { 'page': value - 1, 'per-page': per_page }
    //     this.$router.push({ query })
    //   }
    // },
    // totalPages() {
    //   const per_page = Number(this.$route.query['per-page']) || 10
    //   return Math.ceil(Number(this.total) / per_page)
    // }
  }
}
</script>

<style lang="scss">
// table tag
.v-table {
  min-width: 100%;
  background: #fff;
  border-collapse: collapse;

  // thead tag
  .v-table__head {
    width: 100%;
    background: #fff;

    .v-table__row {
      background: #fff;

      .v-table__cell {
        line-height: 21px;
        font-size: 1rem;
        color: #A3A6B9;
        text-transform: uppercase;

        &:last-child {
          border-right: none;
        }
        .table__filter {
          display: flex;
          align-items: center;
          height: inherit;
          padding: 9px 0;

          .filter__input {
            height: 100%;
            width: calc(100% - 30px);
            padding-bottom: 8px;
            border: none;
            border-bottom: 2px solid #e2e2e2;
            background: transparent;
            font-size: 14px;
            color: #626262;

            &:focus {
              border-color: #7367f0;
            }
          }
          .filter__icon {
            box-sizing: border-box;
            width: 17px;
            height: 17px;
            margin-left: 13px;
            padding: 2px;

            path {
              fill: #333;
            }
          }
        }
      }
    }
  }

  // tbody tag
  .v-table__body {
    width: 100%;
  }

  // All tr tag's
  .v-table__row {
    width: 100%;

    .v-table__cell {
      padding: 1.8rem 0;
      border-bottom: 1px solid #05081D36;
      color: #6A6C78;
    }
  }
}

// &::-webkit-scrollbar {
//   width: 10px;
//   height: 10px;
// }
// &::-webkit-scrollbar-thumb {
//   // border-bottom-left-radius: 6px;
//   // border-bottom-right-radius: 6px;
//   // background-color: #d0d0d0;
//   background: #dae1e7;
//   border-radius: 20px;
// }
// &::-webkit-scrollbar-thumb:hover {
//   background-color: #909090;
// }
</style>
