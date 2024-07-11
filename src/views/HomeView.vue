<script setup>
import { reactive, ref, computed, onMounted } from 'vue'
import { Vue3SeamlessScroll } from "vue3-seamless-scroll";
import * as echarts from 'echarts';
// 第一列的
const datatop = reactive([
   {
      name: '当日销量',
      value: '30'
   },
   {
      name: '当日销量',
      value: '120'
   },
   {
      name: '当日销量',
      value: '359'
   },
   {
      name: '当日销量',
      value: '1390'
   }
]

)
function addCommaToNumber (num) {
   return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
}
const tabsTab = ref(1)
const tabsetData = reactive([
   {
      name: '实时交易详情',
      center: {
         head: [
            {
               title: '交易时间',
            },
            {
               title: "交易地址"
            },
            {
               title: '交易金额'
            }
         ]
      }
   },
   {
      name: '虚拟交易详情',
      center: {
         head: [
            {
               title: '注册时间',
            },
            {
               title: "注册地址"
            },
            {
               title: '注册金额'
            }
         ]
      }
   },
])
const headrow = reactive([

   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   },
   {
      time: '10.00',
      name: '湖北省武汉市江岸区',
      sex: '男'
   }
])
const headtabs = (index) => {
   tabsTab.value = index
}
const headLIst = computed(() => {
   return tabsetData[tabsTab.value].center.head
})


const headdinit = () => {
   let chartDom = document.getElementById('pie');
   let myChart = echarts.init(chartDom);

   const option = {
      tooltip: {
         trigger: 'item',
         formatter: '{a} <br/> {b} : {c} {d}%',
         borderWidth: 0,
         backgroundColor: 'rgba(0,0,0,0.5)',
         textStyle: {
            color: '#fff'
         }
      },
      color: ['#006cff', '#60cda0', '#ed8884', '#ff9f7f', '#0096ff', '#9fe6b8', '#32c5e9', '#1d9dff'],
      series: [
         {
            name: '销售统计',
            type: 'pie',
            radius: ['10%', '70%'],
            center: ['50%', '50%'],
            roseType: 'radius',
            itemStyle: {
               borderRadius: 1
            },
            label: {
               fontSize: 10
            },
            labelLine: {
               length: 4,
               length2: 6
            },
            data: [
               {
                  value: 20,
                  name: '云南',

                  label: {
                     color: '#006cff'
                  }
               },
               {
                  value: 26,
                  name: '北京',
                  label: {
                     color: '#60cda0'
                  }
               },
               {
                  value: 24,
                  name: '山东',
                  label: {
                     color: '#ed8884'
                  }
               },
               {
                  value: 25,
                  name: '河北',
                  label: {
                     color: '#ff9f7f'
                  }
               },
               {
                  value: 20,
                  name: '江苏',
                  label: {
                     color: '#0096ff'
                  }
               },
               {
                  value: 25,
                  name: '浙江',
                  label: {
                     color: '#9fe6b8'
                  }
               },
               {
                  value: 30,
                  name: '四川',
                  label: {
                     color: '#32c5e9'
                  }
               },
               {
                  value: 42,
                  name: '湖北',
                  label: {
                     color: '#1d9dff'
                  }
               }
            ]
         }
      ]
   }
   option && myChart.setOption(option);
   window.addEventListener('resize', () => {
      myChart.resize()
   })
}
onMounted(() => {
   headdinit()
   headbar()
})
// 第二列的
const datatabds = reactive([
   {
      title: '365天',
      center: [
         {
            name: '20,301,987',
            value: '订单量'
         },
         {
            name: '99834',
            value: ' 销售额(万元)'
         }
      ]
   },
   {
      title: '90天',
      center: [
         {
            name: '301,987',
            value: '订单量'
         },
         {
            name: '9834',
            value: ' 销售额(万元)'
         }
      ]
   },
   {
      title: '30天',
      center: [
         {
            name: '1,987',
            value: '订单量'
         },
         {
            name: '3834',
            value: ' 销售额(万元)'
         }
      ]
   },
   {
      title: '24小时',
      center: [
         {
            name: '987',
            value: '订单量'
         },
         {
            name: '837',
            value: ' 销售额(万元)'
         }
      ]
   },
])
const datatabsetrou = ref(0)
const datasety = ref([])
const fometitset = (index) => {
   datatabsetrou.value = index
   datasety.value = datatabds[index].center
   // console.log(datasety.value);
}
setInterval(() => {
   if (datatabsetrou.value >= 3) {
      return (datatabsetrou.value = 0)
   }
   fometitset(datatabsetrou.value+1)

}, 1000)


setTimeout(() => {
   fometitset(0)
}, 0)
const headbar = () => {
   var chartDom = document.getElementById('bar');
   var myChart = echarts.init(chartDom);
   var option;
   option = {
      tooltip: {
         trigger: 'item',
         backgroundColor: 'rgba(0,0,0,0.5)',
         borderColor: 'rgba(0,0,0,0.5)',
         textStyle: {
            color: '#fff'
         },
         // formatter:'{b} : {c} {d}%',
         axisPointer: {
            type: 'shadow'
         },
         borderWidth: 0
      },
      grid: {
         top: '3%',
         left: 0,
         right: '3%',
         bottom: '3%',
         containLabel: true,
         borderColor: 'rgba(0,240,255, 0.3)',
         show: true
      },

      color: {
         type: 'linear',
         x: 0,
         y: 0,
         x2: 0,
         y2: 1,
         colorStops: [
            {
               offset: 1,
               color: '#0068d0' // 0% 处的颜色
            },
            {
               offset: 0,
               color: '#00eff7' // 100% 处的颜色
            }
         ],
         global: false // 缺省为 false
      },
      xAxis: [
         {
            type: 'category',
            data: [
               '上海',
               '⼴州',
               '北京',
               '深圳',
               '合肥',
               '',
               '......',
               '',
               '杭州',
               '厦⻔',
               '济南',
               '成都',
               '重庆'
            ],

            axisTick: {
               show: false
            },
            axisLine: {
               lineStyle: {
                  color: '#4c9bfe'
               }
            }
         }
      ],
      yAxis: {
         type: 'value',
         axisTick: {
            show: false
         },
         axisLine: {
            lineStyle: {
               color: '#4c9bfe'
            }
         },
         splitLine: {
            lineStyle: {
               color: 'rgba(0,240,255, 0.3)'
            }
         }
      },
      series: [
         {
            type: 'bar',
            barWidth: '50%',
            data: [
               2100,
               1900,
               1700,
               1560,
               1400,
               {
                  value: 1200,
                  tooltip: {
                     show: false
                  },
                  emphasis: {
                     itemStyle: {
                        color: 'red'
                     }
                  },
                  itemStyle: {
                     color: '#254065'
                  }
               },
               {
                  value: 1200,
                  tooltip: {
                     show: false
                  },
                  emphasis: {
                     itemStyle: {
                        color: 'red'
                     }
                  },
                  itemStyle: {
                     color: '#254065'
                  }
               },
               {
                  value: 1200,
                  tooltip: {
                     show: false
                  },
                  emphasis: {
                     itemStyle: {
                        color: 'red'
                     }
                  },
                  itemStyle: {
                     color: '#254065'
                  }
               },
               900,
               750,
               600,
               480,
               240
            ]
         }
      ]
   };

   option && myChart.setOption(option);

}

// 第三列的
// 数值的逗号

</script>

<template>
   <!-- 大盒子-->
   <div class="viewport">
      <!-- 第一列-->
      <div class="column">
         <!--  概览-->
         <div class="overview panel">
            <div class="inner">
               <ul class="overviewul">
                  <li v-for="(item, index) in datatop" :key="index" class="overviewli">
                     <span class="overviewtitle">{{ addCommaToNumber(item.value) }}万</span>
                     <span class="overviewname">
                        <i class="overviewi"></i>
                        {{ item.name }}
                     </span>
                  </li>
               </ul>
            </div>
         </div>
         <!-- 交易详情/注册详情-->
         <div class="monitor penster">
            <div class="monitorbox">
               <div class="tabs">
                  <span v-for="(item, index) in tabsetData" :key="index" @click="headtabs(index)"
                     :class="{ tabsactive: index == tabsTab }">{{ item.name }}</span>
               </div>
               <div class="content" style="display: block;">
                  <div class="head">
                     <span class="col" v-for="(item, index) in headLIst" :key="index">{{ item.title }}</span>
                  </div>
                  <div class="marquee-view">
                     <Vue3SeamlessScroll :list="headrow" hover :step="0.3">
                        <div class="row" v-for="(item, index) in headrow" :key="index">
                           <span>{{ item.time }}</span>
                           <span>{{ item.name }}</span>
                           <span>{{ item.sex }}</span>
                           <!-- <span class="rowset"></span> -->
                           <div class="rowset"></div>

                        </div>

                     </Vue3SeamlessScroll>

                  </div>
               </div>
            </div>
         </div>
         <!--  销售地分布统计-->
         <div class="point panel">
            <h3>销售地分布统计</h3>
            <div class="chart">
               <div id="pie" class="pie">
               </div>
               <div class="data">
                  <div class="datatitlte">
                     <h3 class="h3set">320,11</h3>
                     <div class="dataspan">
                        <span class="datastitlerer"></span>
                        <span class="datatitle">销量总数</span>
                     </div>
                  </div>
                  <div class="datatitlte">
                     <h3 class="h3set">320,11</h3>
                     <div class="dataspan">
                        <span class="datastitlerer"></span>
                        <span class="datatitle">销量总数</span>
                     </div>
                  </div>
               </div>
            </div>
         </div>
      </div>
      <!-- 第二列-->
      <div class="column">
         <!--  设备数据统计-->
         <div class="map">设备数据统计</div>
         <!--  用户总量统计-->
         <div class="user panel">
            <h3>用户总量统计</h3>
            <div class="chart">
               <div id="bar" class="pie">
               </div>
               <div class="data">
                  <div class="datatitlte">
                     <h3 class="h3set">320,11</h3>
                     <div class="dataspan">
                        <span class="datastitlerer"></span>
                        <span class="datatitle">销量总数</span>
                     </div>
                  </div>

               </div>
            </div>
         </div>
      </div>
      <!-- 第三列-->
      <div class="column panel">
         <!-- 订单-->
         <div class="order panel">
            <div class="filter">
               <span class="filtertitle" v-for="(item, index) in datatabds" :key="index" @click="fometitset(index)"
                  :class="{ setactive: index == datatabsetrou }">{{
                     item.title }}</span>
            </div>
            <div class="orderdata">
               <div class="orderdatabox" v-for="(item, index) in datasety" :key="index">
                  <h2>{{ item.name }}</h2>
                  <div class="ordertitle">
                     <span class="tittt"></span>
                     <span class="routername">{{ item.value }}</span>
                  </div>
               </div>

            </div>
         </div>
         <!-- 销售-->
         <div class="sales panel">销售</div>
         <!-- 渠道与销售进度-->
         <div class="wrap">
            <div class="channel panel">

            </div>
            <div class="quarter panel">

            </div>
         </div>
         <!-- 排行-->
         <div class="top panel">排行</div>
      </div>
   </div>
</template>

<style lang="scss" scoped>
.viewport {
   max-width: 1920px;
   min-width: 1080px;
   height: 100%;
   margin: 0 auto;
   background: url('@/assets/images/logo.png') no-repeat;
   background-size: contain;
   color: #fff;
   display: flex;
   box-sizing: border-box;
   padding: .4948rem .1042rem 0;
}





.column:nth-child(2) {
   flex: 4;
   margin: .1667rem .1042rem;

   .map {
      height: 3.0104rem;
      margin-bottom: .1042rem;
      // background: rgba(0,0,0,0.5);
      background-color: red;
   }

   .user {
      height: 1.7708rem;
   }
}
</style>
