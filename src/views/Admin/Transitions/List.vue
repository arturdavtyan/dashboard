<template>
  <div class="container-view__inner w-full">
    <div class="container-view__tools flex items-center justify-between">
      <div class="container-view__buttons flex items-center">
        <div class="container-view__button">
          <img class="calendar absolute" :src="calendar" alt="Calendar">
          <primary-dark-button>ADD MEETING(S)</primary-dark-button>
        </div>
        <div class="container-view__button">
          <img class="check absolute" :src="check" alt="Check">
          <primary-button>SELECT ALL</primary-button>
        </div>
        <div class="container-view__button">
          <img class="plus absolute" :src="plus" alt="Plus">
          <primary-button :disabled="true">ADD TO SCOPE</primary-button>
        </div>
        <div class="container-view__button">
          <img class="minus absolute" :src="minus" alt="Minus">
          <primary-button :disabled="true">MARK AS UNSCOPE</primary-button>
        </div>
      </div>
      <div class="container-view__sort-box">
        <div class="container-view__sort flex items-center">
          <span class="container-view__sort-by">sort by</span>
          <span class="container-view__sort-title flex items-center">
            Date added
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 13 7.707"><path class="a" d="M239.646,500.561l-6-6a.5.5,0,0,1,0-.708l.706-.706a.5.5,0,0,1,.708,0L240,498.086l4.939-4.939a.5.5,0,0,1,.708,0l.706.706a.5.5,0,0,1,0,.708l-6,6A.5.5,0,0,1,239.646,500.561Z" transform="translate(-233.5 -493)"/>
            </svg>
          </span>
        </div>
      </div>
    </div>
    <div class="container-view__list">
      <div class="container-view__list--inner w-full h-full">
        <!-- <v-table :headersData="tableHeaders"></v-table> -->
        <v-table :header="tableHeaders">
          <v-tr
            v-for="(item, index) in tableContent"
            :key="`item-${index}`"
          >
            <v-td class="p-0"><div class="flex items-center"><input class="checkbox" type="checkbox"></div></v-td>
            <v-td class="subject text-bold">{{ item.subject }}</v-td>
            <v-td>{{ item.organizer }}</v-td>
            <v-td>{{ item.date }}</v-td>
            <v-td>{{ item.time }}</v-td>
            <v-td>{{ item.type }}</v-td>
            <v-td>{{ item.frequency }}</v-td>
            <v-td>{{ item.note }}</v-td>
            <v-td class="p-0">
              <div class="flex items-center">
                <img class="outlook-icon" src="https://i.pinimg.com/originals/93/ed/fa/93edfaf973bc2bad4b091228ae540dff.png" alt="outlook">
              </div>
            </v-td>
            <v-td class="p-0">
              <button class="status-btn">Scoped</button>
            </v-td>
          </v-tr>
        </v-table>
      </div>
    </div>
  </div>
</template>

<script>
import calendarSvg from '@/assets/svgs/calendar.svg'
import checkSvg from '@/assets/svgs/check.svg'
import plusSvg from '@/assets/svgs/plus.svg'
import minusSvg from '@/assets/svgs/minus.svg'

export default {
  computed: {
    calendar () { return calendarSvg },
    check () { return checkSvg },
    plus () { return plusSvg },
    minus () { return minusSvg }
  },
  data () {
    return {
      tableHeaders: [
        {
          name: '',
          width: 44
        },
        {
          name: 'Subject',
          width: 200
        },
        {
          name: 'Organizer',
          width: 210
        },
        {
          name: 'Date',
          width: 190
        },
        {
          name: 'Time',
          width: 160
        },
        {
          name: 'Type',
          width: 160
        },
        {
          name: 'Frequency',
          width: 180
        },
        {
          name: 'Note',
          width: 170
        },
        {
          name: 'source',
          width: 100
        },
        {
          name: 'status',
          width: 102,
          fixed: true
        }
      ],
      tableContent: [
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        },
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        },
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        },
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        },
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        },
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        },
        {
          subject: 'Lorem ipsum dolor',
          organizer: 'Lorem ipsum dolor sit',
          date: 'October 6, 2020',
          time: '10:30 am',
          type: 'Recurring',
          frequency: 'Low',
          note: 'Lorem ipsum dolor'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.container-view__inner {
  border-top: 1px solid #05081D36;

  .container-view__tools {
    padding: 1.58rem 0;

    .container-view__buttons {

      .container-view__button {
        position: relative;
        width: 220px;

        &:not(:last-child) {
          margin-right: 10px;
        }
        .calendar {
          top: 1rem;
          left: 1rem;
        }
        .check {
          top: 1.28rem;
          left: 1.13rem;
        }
        .plus {
          top: 1.21rem;
          left: 0.85rem;
        }
        .minus {
          top: 1.65rem;
          left: 0.92rem;
        }
      }
    }

    .container-view__sort-box {

      .container-view__sort {

        .container-view__sort-by {
          margin-right: 1rem;
          font-size: 1rem;
          text-transform: uppercase;
          color: #A3A6B9;
        }
        .container-view__sort-title {
          font-size: 0.866rem;
          color: #05081D;
          cursor: pointer;

          svg {
            width: 13px;
            height: 7.707px;
            margin-left: 0.477rem;

            .a{fill:#05081d;}
          }
        }
      }
    }
  }

  .container-view__list {
    width: 100%;
    height: 602px;
    padding: 0 1.8rem;
    border-radius: 30px;
    background-color: #fff;

    .container-view__list--inner {
      overflow: auto;

      .subject {
        color: #05081D;
      }
      .checkbox {
        width: 26px;
        height: 26px;
        border-radius: 5px;
        border: 1px solid #A3A6B9;
      }
      .outlook-icon {
        width: 36px;
      }
      .status-btn {
        width: 100%;
        height: 36px;
        border-radius: 18px;
        background-color: $primary;
        color: #fff;
      }
    }
  }
}
</style>
