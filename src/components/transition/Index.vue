<template>
  <div class="trnasition-conponent relative">
    <div :class="`color-for-status absolute ${statusColor}`"></div>
    <div class="trnasition-conponent__top flex">

      <div class="trnasition-conponent__top--name flex items-center col-1">
        {{ item.name }}
        <img v-if="item.icon" class="h-6 ml-7" :src="item.icon" :alt="item.icon">
      </div>

      <div class="trnasition-conponent__top--role col-2">
        <div class="trnasition-conponent__title space-between">my role</div>
        <div class="role-name text">{{ item.role }}</div>
      </div>

      <div class="trnasition-conponent__top--status col-3">
        <div class="trnasition-conponent__title space-between">status</div>
        <div :class="`status-view ${statusColor}`">{{ item.status }}</div>
      </div>

      <div class="trnasition-conponent__top--days-to-go col-4">
        <div class="trnasition-conponent__title space-between">days to go</div>
        <div class="role-name text">{{ item.daysToGo }}</div>
      </div>

      <div class="-mt-2 col-5 flex items-center justify-between">
        <div class="flex items-center">{{ item.comments }} <img class="ml-3" :src="comment" alt="Comment"></div>
        <div
          class="angle-down ml-8 cursor-pointer"
          :class="{ 'rotate': isShow }"
          @click="isShow = !isShow"><img :src="angleDown" alt="Angle down"></div>
      </div>

    </div>
    <div :class="{ 'open pt-3 pb-3': isShow }" class="trnasition-conponent__bottom">

      <div class="row flex items-center">
        <div class="col-1 mt-2">
          <div class="trnasition-conponent__title space-between-5">creator</div>
          <div class="text">{{ item.creator }}</div>
        </div>
        <div class="col-2 mt-2">
          <div class="trnasition-conponent__title space-between-5">collaborator(s)</div>
          <div class="text">
            <template v-for="(person, index) in item.collaborators">
              <span :key="`person-${index}`" v-if="index === 0">{{ person.name }}</span>
              <span :key="`person-${index}`" v-else>{{ ` | ${person.name}` }}</span>
            </template>
          </div>
        </div>
        <div class="col-3 mt-2">
          <div class="trnasition-conponent__title space-between-5">transitor</div>
          <div class="text">{{ item.transitor }}</div>
        </div>
        <div class="col-4 mt-2">
          <div class="trnasition-conponent__title space-between-5">transitee(s)</div>
          <div class="text">
            <template v-for="(person, index) in item.transitees">
              <span :key="`person-${index}`" v-if="index === 0">{{ person.name }}</span>
              <span :key="`person-${index}`" v-else>{{ ` | ${person.name}` }}</span>
            </template>
          </div>
        </div>
        <div class="col-5 flex items-center justify-end">
          <img :src="send" alt="Send">
        </div>
      </div>

      <div class="row flex items-center">
        <div class="col-6 flex items-center">
          <span :class="`completition-percentage mr-6 ${statusFontColor}`">completion percentage</span>
          <div class="completion-percentage__progress">
            <div
              :class="`completion-percentage__progress--fill relative ${statusColor}`"
              :style="{ width: `${item.completionPercentage}%` }">
              <span :class="`progress-percent ${statusFontColor}`">{{ `${item.completionPercentage} %` }}</span>
            </div>
          </div>
        </div>
        <div class="col-5 flex items-center justify-end">
          <img :src="eye" alt="Eye">
        </div>
      </div>

      <div class="row flex items-center">
        <div class="col-1">
          <div class="trnasition-conponent__title space-between-5">tAsKS</div>
          <div class="text">{{ item.tasks }}</div>
        </div>
        <div class="col-2">
          <div class="trnasition-conponent__title space-between-5">knowledge transefer</div>
          <div class="text">{{ item.knowledgeTransfer }}</div>
        </div>
        <div class="col-3">
          <div class="trnasition-conponent__title space-between-5">production parallel</div>
          <div class="text">{{ item.productionParallel }}</div>
        </div>
        <div class="col-4">
          <div class="trnasition-conponent__title space-between-5">LIVE EXECUTION</div>
          <div class="text">{{ item.liveExecution }}</div>
        </div>
        <div class="col-5 flex items-center justify-end">
          <img :src="check" alt="Check">
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import commentSvg from '@/assets/svgs/comment.svg'
import angleDown from '@/assets/svgs/angle-down.svg'

import sendSvg from '@/assets/svgs/send.svg'
import eyeSvg from '@/assets/svgs/eye.svg'
import checkSvg from '@/assets/svgs/check-circle.svg'

export default {
  props: ['item'],
  data () {
    return {
      isShow: false
    }
  },
  computed: {
    statusColor () {
      switch (this.item.status) {
        case 'ready to be concluded':
          return 'rose'
        case 'production parallel':
          return 'indigo'
        case 'knowledge transfer':
          return 'cyan'
        default:
          return 'rose'
      }
    },
    statusFontColor () {
      switch (this.item.status) {
        case 'ready to be concluded':
          return 'font-rose'
        case 'production parallel':
          return 'font-indigo'
        case 'knowledge transfer':
          return 'font-cyan'
        default:
          return 'font-rose'
      }
    },
    comment () { return commentSvg },
    angleDown () { return angleDown },
    send () { return sendSvg },
    eye () { return eyeSvg },
    check () { return checkSvg }
  }
}
</script>

<style lang="scss" scoped>
.trnasition-conponent {
  margin-bottom: 15px;
  padding-left: 69px;
  padding-right: 37px;
  border-radius: 30px;
  box-shadow: 0 0 18px 5px #00000010;
  background-color: #fff;
  overflow: hidden;

  &:last-child {
    margin-bottom: 7.5px;
  }

  .rose {
    background-color: #F53361;
  }
  .indigo {
    background-color: #6D32A5;
  }
  .cyan {
    background-color: #43BCCD;
  }
  .font-rose {
    color: #F53361;
  }
  .font-indigo {
    color: #6D32A5;
  }
  .font-cyan {
    color: #43BCCD;
  }
  .rotate {
    transform: rotateX(180deg);
  }

  .col-1 {
    flex-basis: 26%;
  }
  .col-2 {
    flex-basis: 22%;
  }
  .col-3 {
    flex-basis: 22%;
  }
  .col-4 {
    flex-basis: 22%;
  }
  .col-5 {
    flex-basis: 8%;
  }
  .col-6 {
    flex-basis: 92%;
  }

  .trnasition-conponent__title {
    font-size: 0.8rem;
    font-weight: bold;
    text-transform: uppercase;
    color: #A3A6B9;

    &.space-between {
      margin-bottom: 12px;
    }
    &.space-between-5 {
      margin-bottom: 5px;
    }

    ~ .text {
      font-size: 1rem;
      font-weight: bold;
      color: #05081D;
    }
  }

  .color-for-status {
    top: 0;
    left: 0;
    width: 17px;
    height: 100%;
    z-index: 100;
  }

  .trnasition-conponent__top {
    width: 100%;
    height: 93px;
    padding-top: 18px;

    .trnasition-conponent__top--name {
      font-size: 1.7rem;
      font-weight: bold;
      transform: translateY(-9px);
    }
    .trnasition-conponent__top--status {

      .status-view {
        // width: 228px;
        display: inline-block;
        height: 30px;
        padding: 0 15px;
        line-height: 30px;
        transform: translate(-15px, -9px);
        border-radius: 15px;
        font-size: 1rem;
        font-weight: bold;
        text-transform: uppercase;
        color: #fff;
      }
    }
    .angle-down {
      transition: 0.4s;
    }
  }
  .trnasition-conponent__bottom {
    width: 100%;
    height: 0;
    transition: 0.4s;

    &.open {
      height: 197px;
      border-top: 1px solid #efefef;
    }
    .row:not(:last-child) {
      margin-bottom: 5px;
    }

    .completition-percentage {
      font-size: 0.8rem;
      font-weight: bold;
      text-transform: uppercase;
    }
    .completion-percentage__progress {
      flex-grow: 1;
      height: 10px;
      background-color: #eee;
      border-radius: 40px;

      .completion-percentage__progress--fill {
        height: 100%;
        border-radius: 40px;

        .progress-percent {
          position: absolute;
          top: -24px;
          right: 0;
        }
      }
    }
  }
}
</style>
