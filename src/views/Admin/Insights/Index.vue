<template>
  <div class="container-view">
    <div class="header flex items-center justify-between">
      <span class="section-name">Insights</span>
      <div class="statistics flex items-center justify-between">
        <div class="statistics__item">
          <div class="item__top flex items-center">
            <span class="item__top--title">total transitions</span>
          </div>
          <div class="item__bottom">
            <h4>15</h4>
          </div>
        </div>
        <div class="statistics__item">
          <div class="item__top flex items-center">
            <span class="item__top--title">INITIATED</span>
            <img class="ml-2" :src="info" alt="Info">
          </div>
          <div class="item__bottom">
            <h4>2</h4>
          </div>
        </div>
        <div class="statistics__item">
          <div class="item__top flex items-center">
            <span class="item__top--title">IN PROGRESS</span>
            <img class="ml-2" :src="info" alt="Info">
          </div>
          <div class="item__bottom">
            <h4>5</h4>
          </div>
        </div>
        <div class="statistics__item">
          <div class="item__top flex items-center">
            <span class="item__top--title">completed</span>
            <img class="ml-2" :src="info" alt="Info">
          </div>
          <div class="item__bottom">
            <h4>2</h4>
          </div>
        </div>
      </div>
    </div>

    <div class="container-view__inner">

      <div class="concludition-container cntn-block box flex ietms-center justify-between">
        <div class="concludition-container__left pr-8 flex items-center">
          <img :src="flag" alt="Flag">
          <div class="concludition-container__content">
            <h5>Transition ready to be concluded</h5>
            <span class="concludition-container__text">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et</span>
          </div>
        </div>
        <div class="concludition-container__right flex items-center">
          <div class="concludition-container__btn">
            <primary-dark-button>ADD OTHER TASKS</primary-dark-button>
          </div>
          <div class="concludition-container__btn">
            <primary-rose-button>CONCLUDE TRANSITION</primary-rose-button>
          </div>
        </div>
      </div>

      <!-- First block -->
      <div class="flex items-center cntn-block">

        <div class="transitions-state box">

          <div class="flex items-center">
            <span class="header__title mr-5">transitions state</span>
            <div class="custom-select flex items-center">
              <span class="custom-select__target">All</span>
              <img class="custom-select__arrow-down" :src="arrowDown" alt="Arrow down">
            </div>
            <span class="header__title ml-4 mr-4">|</span>
            <div class="custom-select flex items-center">
              <span class="custom-select__target">Current state</span>
              <img class="custom-select__arrow-down" :src="arrowDown" alt="Arrow down">
            </div>
          </div>

          <div class="trnasitions-state__chart w-full" ref="trnasitionsState"></div>

        </div>

        <div class="due-date box">

          <div class="flex items-center">
            <span class="header__title mr-5">due date</span>
            <div class="custom-select flex items-center">
              <span class="custom-select__target">All</span>
              <img class="custom-select__arrow-down" :src="arrowDown" alt="Arrow down">
            </div>
          </div>

          <div class="due-date__chart w-full" ref="dueDate"></div>
        </div>

      </div>

      <!-- Second block -->
      <div class="flex items-center cntn-block">

        <div class="tasks-review-rate box">

          <div class="flex items-center">
            <span class="header__title mr-5">tasks review rate</span>
            <div class="custom-select flex items-center">
              <span class="custom-select__target">All phases</span>
              <img class="custom-select__arrow-down" :src="arrowDown" alt="Arrow down">
            </div>
          </div>

          <div class="tasks-review-rate__chart w-full" ref="tasksReviewRate"></div>
        </div>

        <div class="transitions-state box">

          <div class="flex items-center">
            <span class="header__title mr-5">completion rate</span>
            <div class="custom-select flex items-center">
              <span class="custom-select__target">All</span>
              <img class="custom-select__arrow-down" :src="arrowDown" alt="Arrow down">
            </div>
            <span class="header__title ml-4 mr-4">|</span>
            <div class="custom-select flex items-center">
              <span class="custom-select__target">Current state</span>
              <img class="custom-select__arrow-down" :src="arrowDown" alt="Arrow down">
            </div>
          </div>

          <div class="completion-rate__chart w-full" ref=""></div>

        </div>

      </div>

      <div class="recent-transitions cntn-block box">
        <div class="recent-transitions__header flex items-ceneter justify-between">
          <span class="recent-transitions__name">recent transitions</span>
          <div class="recent-transitions__switch flex items-center">
            <span class="switch-title">Hide completed</span>
            <label class="switch">
              <input type="checkbox" checked>
              <span class="slider round"></span>
            </label>
          </div>
        </div>
        <div class="recent-transitions__accordion">
          <trnasition-component
            v-for="item in recentTransitions"
            :key="item.id"
            :item="item" />
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import info from '@/assets/svgs/circle-info.svg'
import flag from '@/assets/svgs/flag.svg'
import arrowDown from '@/assets/svgs/angle-down.svg'

import * as am4core from '@amcharts/amcharts4/core'
import * as am4charts from '@amcharts/amcharts4/charts'
import am4themesAnimated from '@amcharts/amcharts4/themes/animated'

am4core.useTheme(am4themesAnimated)

export default {
  components: {
    trnasitionComponent: () => import('@/components/transition/Index.vue')
  },
  computed: {
    info () { return info },
    flag () { return flag },
    arrowDown () { return arrowDown }
  },
  data () {
    return {
      recentTransitions: [
        {
          id: 1,
          name: 'UI/UX Designer',
          role: 'Creator',
          status: 'ready to be concluded',
          daysToGo: 26,
          comments: 15,
          icon: flag,
          creator: 'John Adams',
          collaborators: [{ name: 'Nishant Mehra' }, { name: 'Lu Shih' }],
          transitor: 'Sammy Jo',
          transitees: [{ name: 'Vladimir Nikolsky' }],
          completionPercentage: 100,
          tasks: 26,
          knowledgeTransfer: 12,
          productionParallel: 6,
          liveExecution: 'N/A'
        },
        {
          id: 2,
          name: 'Tech Lead',
          role: 'Collaborator',
          status: 'production parallel',
          daysToGo: 26,
          comments: 15,
          icon: null,
          creator: 'John Adams',
          collaborators: [{ name: 'Nishant Mehra' }, { name: 'Lu Shih' }],
          transitor: 'Sammy Jo',
          transitees: [{ name: 'Vladimir Nikolsky' }],
          completionPercentage: 60,
          tasks: 26,
          knowledgeTransfer: 12,
          productionParallel: 6,
          liveExecution: 'N/A'
        },
        {
          id: 3,
          name: 'HR Manager',
          role: 'Transitor',
          status: 'knowledge transfer',
          daysToGo: 26,
          comments: 15,
          icon: null,
          creator: 'John Adams',
          collaborators: [{ name: 'Nishant Mehra' }, { name: 'Lu Shih' }],
          transitor: 'Sammy Jo',
          transitees: [{ name: 'Vladimir Nikolsky' }],
          completionPercentage: 88,
          tasks: 26,
          knowledgeTransfer: 12,
          productionParallel: 6,
          liveExecution: 'N/A'
        }
      ],

      chartData: [
        {
          state: 'Completed due date',
          value: 3,
          color: am4core.color('#43BCCD')
        }, {
          state: 'Nearing due date',
          value: 2,
          color: am4core.color('#6D32A5')
        }
      ],
      tasksReviewRate: [
        {
          state: 'Reviewed tasks',
          value: 26,
          color: am4core.color('#43BCCD')
        }, {
          state: 'Not reviewed tasks',
          value: 18,
          color: am4core.color('#6D32A5')
        }
      ],
      TransitionsStateChartData: [
        {
          country: 'USA',
          visits: 1,
          color: am4core.color('#1FC599')
        },
        {
          country: 'China',
          visits: 5,
          color: am4core.color('#43BCCD')
        },
        {
          country: 'Japan',
          visits: 4,
          color: am4core.color('#6D32A5')
        },
        {
          country: 'Germany',
          visits: 3,
          color: am4core.color('#F53361')
        },
        {
          country: 'UK',
          visits: 2,
          color: am4core.color('#F2A201')
        }
      ],
      completionRate: [
        {
          category: 'Place #1',
          first: 40,
          second: 55,
          third: 60
        },
        {
          category: 'Place #2',
          first: 30,
          second: 78,
          third: 69
        },
        {
          category: 'Place #3',
          first: 27,
          second: 40,
          third: 45
        },
        {
          category: 'Place #4',
          first: 50,
          second: 33,
          third: 22
        }
      ]
    }
  },

  mounted () {
    this.TransitionsStateChart()
    this.PieChart('dueDate', this.chartData)
    this.PieChart('tasksReviewRate', this.tasksReviewRate)
  },

  beforeDestroy () {
    if (this.chart) {
      this.chart.dispose()
    }
  },

  methods: {
    TransitionsStateChart () {
      const chart = am4core.create(this.$refs.trnasitionsState, am4charts.XYChart)

      chart.data = this.TransitionsStateChartData

      chart.padding(40, 0, 0, 0)

      const categoryAxis = chart.xAxes.push(new am4charts.CategoryAxis())
      categoryAxis.renderer.grid.template.location = 0
      categoryAxis.dataFields.category = 'country'
      categoryAxis.renderer.minGridDistance = 0
      // categoryAxis.renderer.inversed = false

      categoryAxis.renderer.grid.template.disabled = true

      const valueAxis = chart.yAxes.push(new am4charts.ValueAxis())
      valueAxis.min = 0
      // valueAxis.extraMax = 0.15
      // valueAxis.rangeChangeEasing = am4core.ease.linear
      // valueAxis.rangeChangeDuration = 1500

      const series = chart.series.push(new am4charts.ColumnSeries())
      series.dataFields.categoryX = 'country'
      series.dataFields.valueY = 'visits'
      // series.tooltipText = '{valueY.value}'
      series.columns.template.strokeOpacity = 0
      series.columns.template.width = 65

      series.columns.template.column.cornerRadiusTopRight = 13
      series.columns.template.column.cornerRadiusTopLeft = 13
      series.columns.template.column.cornerRadiusBottomRight = 13
      series.columns.template.column.cornerRadiusBottomLeft = 13
      // series.interpolationDuration = 1500
      // series.interpolationEasing = am4core.ease.linear
      const labelBullet = series.bullets.push(new am4charts.LabelBullet())
      labelBullet.label.verticalCenter = 'bottom'
      labelBullet.label.dy = -10
      // labelBullet.label.text = '{values.valueY.workingValue.formatNumber("#.")}'

      chart.zoomOutButton.disabled = true

      // pieSeries.slices.template.propertyFields.fill = 'color'

      // as by default columns of the same series are of the same color, we add adapter which takes colors from chart.colors color set
      series.columns.template.adapter.add('fill', function (fill, target) {
        return chart.data[target.dataItem.index].color
      })

      // categoryAxis.sortBySeries = series
    },
    PieChart (container, data) {
      const chart = am4core.create(this.$refs[container], am4charts.PieChart)

      chart.data = data

      chart.innerRadius = am4core.percent(50) // 47px

      const pieSeries = chart.series.push(new am4charts.PieSeries())
      pieSeries.dataFields.value = 'value'
      pieSeries.dataFields.category = 'state'
      pieSeries.slices.template.propertyFields.fill = 'color'

      // Disable ticks and labels
      pieSeries.labels.template.disabled = true
      pieSeries.ticks.template.disabled = true

      // Add a legend
      chart.legend = new am4charts.Legend()
      chart.legend.position = 'left'
      chart.legend.maxWidth = undefined
      chart.legend.fontSize = '0.86rem'

      const marker = chart.legend.markers.template.children.getIndex(0)
      marker.cornerRadius(12, 12, 12, 12)
    }
  }

}
</script>

<style lang="scss" scoped>
.header {
  margin-bottom: 2.358rem;

  .section-name {
    font-size: 4rem;
    letter-spacing: 0px;
    font-weight: bold;
  }

  .statistics {
    width: 821px;

    .statistics__item {

      .item__top {

        .item__top--title {
          padding-top: 2px;
          text-transform: uppercase;
          color: #A3A6B9;
        }
      }
      .item__bottom {

        h4 {
          font-size: 2rem;
          color: #05081D;
          font-weight: 100;
        }
      }
    }
  }
}

.header__title {
  text-transform: uppercase;
  color: #A3A6B9;
}

.custom-select {

  .custom-select__target {
    font-size: 0.8666rem;
    color: #05081D;
  }
  .custom-select__arrow-down {
    width: 13px;
    height: auto;
    margin-left: 5.5px;
  }
}

.container-view__inner {
  padding-top: 2.38rem;
  border-top: 1px solid #05081D36;

  .cntn-block:not(:last-child) {
    margin-bottom: 20px;
  }

  .transitions-state {
    flex-basis: calc(65% - 26px);
    margin-right: 26px;

    .trnasitions-state__chart {
      height: 309px;
    }
  }
  .due-date {
    flex-basis: 35%;

    .due-date__chart {
      height: 309px;
      padding: 17px 0;
    }
  }

  .tasks-review-rate {
    flex-basis: 35%;
    margin-right: 26px;

    .tasks-review-rate__chart {
      height: 309px;
      padding: 17px 0;
    }
  }
  .completion-rate {
    flex-basis: calc(65% - 26px);

    .completion-rate__chart {
      height: 309px;
    }
  }

  .concludition-container {

    .concludition-container__left {

      .concludition-container__content {
        margin-left: 1.19rem;

        h5 {
          margin-bottom: 3px;
          font-size: 1.73rem;
          color: #05081D;
        }
        .concludition-container__text {
          // margin-right: 30px;
          font-size: 0.866rem;
          color: #A3A6B9;
          letter-spacing: 0;
        }
      }
    }
    .concludition-container__right {

      .concludition-container__btn {
        // width: 100%;
        width: 441px;
        // flex-basis: 441px;
        // flex-grow: 1;

        &:not(:first-child) {
          margin-left: 10px;
        }
      }
    }
  }

  .recent-transitions {

    .recent-transitions__header {
      margin-bottom: 26px;

      .recent-transitions__name {
        font-size: 1rem;
        color: #A3A6B9;
        text-transform: uppercase;
      }
      .recent-transitions__switch {

        .switch-title {
          margin-right: 17px;
          font-size: 0.866rem;
          color: #05081D;
        }
        .switch {
          position: relative;
          display: inline-block;
          width: 33px;
          height: 18px;

          input {
            opacity: 0;
            width: 0;
            height: 0;

            &:checked + .slider {
              background-color: #6D32A5;
            }
            &:checked + .slider:before {
              -webkit-transform: translateX(15px);
              -ms-transform: translateX(15px);
              transform: translateX(15px);
            }
          }
          .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            border-radius: 34px;
            background-color: #ccc;
            -webkit-transition: .4s;
            transition: .4s;

            &:before {
              position: absolute;
              content: "";
              height: 16px;
              width: 16px;
              left: 1px;
              bottom: 1px;
              // left: -10px;
              // bottom: 1px;
              border-radius: 50%;
              background-color: white;
              -webkit-transition: .4s;
              transition: .4s;
            }
          }
        }
      }
    }
  }
}
</style>
