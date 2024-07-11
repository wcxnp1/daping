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
   headline()
   headradar()
   headgauge()
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
   fometitset(datatabsetrou.value + 1)

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

const salestitletabs = ref([
   {
      name: '年'
   },
   {
      name: '季'
   },
   {
      name: '月'
   },
   {
      name: '周'
   }
])
const setlesdata = ref(
   [
      {
         conter: {
            name: [24, 40, 351, 134, 90, 230, 235, 230, 134, 230, 235, 134],
            value: [24, 40, 351, 134, 90, 230, 235, 230, 134, 230, 235, 134]
         }
      },
      {
         conter: {
            name: [30, 50, 351, 134, 34, 230, 235, 230, 134, 230, 235, 134],
            value: [24, 40, 351, 12, 34, 230, 235, 230, 120, 230, 235, 120]
         }
      },
      {
         conter: {
            name: [12, 40, 351, 12, 90, 230, 235, 230, 120, 230, 235, 120],
            value: [12, 40, 121, 12, 6, 230, 212, 230, 120, 120, 212, 120]
         }
      },
      {
         conter: {
            name: [12, 40, 121, 12, 6, 120, 212, 120, 120, 230, 210, 120],
            value: [24, 40, 101, 134, 6, 230, 210, 230, 120, 230, 210, 120]
         }
      }


   ]
)
const salestitletab = ref(0)
const setdata = ref([])
const Xdata = ref([])
const Ydata = ref([])
function headtabssales (index) {
   clearInterval(remoteccolor)
   salestitletab.value = index
   setdata.value = setlesdata.value[index].conter
   Xdata.value = setdata.value.name
   Ydata.value = setdata.value.value
   headline()

}
setTimeout
   (() => {
      headtabssales(0)
   })
function remoteccolor () {
   return setInterval
      (() => {
         salestitletab.value++
         if (salestitletab.value > 3) {
            salestitletab.value = 0
         }
         headtabssales(salestitletab.value)
      }, 4000)
}
remoteccolor()
const headline = () => {
   const myChart = echarts.init(document.getElementById('line'));
   const option = {
      tooltip: {
         trigger: "axis"
      },
      color: ['#00f2f1', '#ed3f35'],
      legend: {
         data: ["预期销售额", "实际销售额"],
         textStyle: {
            color: '#4c9bfd' // 图例⽂字颜⾊
         },
         right: '10%' // 距离右边10%
      },
      grid: {
         top: '20%',
         left: '3%',
         right: '4%',
         bottom: '3%',
         show: true,// 显示边框
         borderColor: '#012f4a',// 边框颜⾊
         containLabel: true // 包含刻度⽂字在内
      },
      xAxis: {
         type: 'category',
         data: ['1⽉', '2⽉', '3⽉', '4⽉', '5⽉', '6⽉', '7⽉', '8⽉', '9⽉', '10⽉', '11⽉', '12⽉'],
         axisTick: {
            show: false // 去除刻度线
         },
         axisLabel: {
            color: '#4c9bfd' // ⽂本颜⾊
         },
         axisLine: {
            show: false // 去除轴线
         },
         boundaryGap: false // 去除轴内间距
      },
      yAxis: {

         type: 'value',
         axisTick: {
            show: false // 去除刻度
         },
         axisLabel: {
            color: '#4c9bfd' // ⽂字颜⾊
         },
         splitLine: {
            lineStyle: {
               color: '#012f4a' // 分割线颜⾊
            }
         }

      },
      series: [
         {
            name: '预期销售额',
            data: Xdata.value,
            type: 'line',
            // 折线修饰为圆滑
            smooth: true,
         }, {
            name: '实际销售额',
            data: Ydata.value,
            type: 'line',
            smooth: true,
         }
      ]
   };
   // 3. 把配置和数据给实例对象
   myChart.setOption(option);

}
const headradar = () => {
   const myChart = echarts.init(document.getElementById('radar'));
   // 2.指定配置
   var option = {
      tooltip: {
         show: true,
         // 控制提示框组件的显示位置
         position: ["60%", "10%"]
      },
      radar: {
         indicator: [
            { name: "机场", max: 100 },
            { name: "商场", max: 100 },
            { name: "⽕⻋站", max: 100 },
            { name: "汽⻋站", max: 100 },
            { name: "地铁", max: 100 }
         ],
         // 修改雷达图的⼤⼩
         radius: "65%",
         shape: "circle",
         // 分割的圆圈个数
         splitNumber: 4,
         name: {
            // 修饰雷达图⽂字的颜⾊
            textStyle: {
               color: "#4c9bfd"
            }
         },
         // 分割的圆圈线条的样式
         splitLine: {
            lineStyle: {
               color: "rgba(255,255,255, 0.5)"
            }
         },
         splitArea: {
            show: false
         },
         // 坐标轴的线修改为⽩⾊半透明
         axisLine: {
            lineStyle: {
               color: "rgba(255, 255, 255, 0.5)"
            }
         }
      },
      series: [
         {
            name: "北京",
            type: "radar",
            // 填充区域的线条颜⾊
            lineStyle: {
               normal: {
                  color: "#fff",
                  width: 1,
                  opacity: 0.5
               }
            },

            data: [[90, 19, 56, 11, 34]],
            // 设置图形标记 （拐点）
            symbol: "circle",
            // 这个是设置⼩圆点⼤⼩
            symbolSize: 5,
            // 设置⼩圆点颜⾊
            itemStyle: {
               color: "#fff"
            },
            // 让⼩圆点显示数据
            label: {
               show: true,
               fontSize: 10
            },
            // 修饰我们区域填充的背景颜⾊
            areaStyle: {
               color: "rgba(238, 197, 102, 0.6)"
            }
         }
      ]
   }
   // 3.把配置和数据给对象
   myChart.setOption(option);
   // 当我们浏览器缩放的时候，图表也等⽐例缩放
   window.addEventListener("resize", function () {
      // 让我们的图表调⽤ resize这个⽅法
      myChart.resize();
   });
}
const headgauge = () => {
   var myChart = echarts.init(document.getElementById('gauge'));
   var option = {
      series: [
         {
            type: 'pie',
            // 放⼤图形
            radius: ['130%', '150%'],
            // 移动下位置 套住50%⽂字
            center: ['48%', '80%'],
            label: {
               normal: {
                  show: false
               }
            },
            // 起始⻆度，⽀持范围[0, 360]
            startAngle: 180,
            hoverOffset: 0,


            data: [
               {
                  value: 10,
                  itemStyle: {
                     // 颜⾊渐变#00c9e0->#005fc1
                     color: new echarts.graphic.LinearGradient(
                        // (x1,y2) 点到点 (x2,y2) 之间进⾏渐变
                        0,
                        0,
                        0,
                        1,
                        [
                           { offset: 0, color: "#00c9e0" }, // 0 起始颜⾊
                           { offset: 1, color: "#005fc1" } // 1 结束颜⾊
                        ]
                     )
                  }
               },
               { value: 100, itemStyle: { color: '#12274d' } }, // 颜⾊#12274d

            ]
         }
      ]
   }
   // 3. 把数据和配置给实例对象
   myChart.setOption(option);
}


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
         <div class="sales panel">
            <div class="salesdata">
               <h3>销售额统计</h3>
               <span class="salestitle" v-for="(item, index) in salestitletabs" :key="index"
                  @click="headtabssales(index)" :class="{ saleeactive: salestitletab == index }">{{
                     item.name }}</span>
            </div>
            <div class="chartselad">
               <!-- <div class="label">单位:万</div> -->
               <div class="line" id="line">
               </div>
            </div>
         </div>
         <!-- 渠道与销售进度-->
         <div class="wrap">
            <div class="channel panel">
               <h3>渠道分布</h3>
               <div class="radar" id="radar"></div>
            </div>
            <div class="quarter panel">
               <h3>一季度销售进度</h3>
               <div class="quarterbie" id="gauge"></div>
               <div class="potingauge">50%</div>
               <div class="quarterbox">
                  <div class="boxetser">
                     <span>1,321</span>
                     <div class="boxserter">
                        <span class="quartercolor"></span>
                        <span class="quartertitle">销售额(万元)</span>
                     </div>
                  </div>
                  <div class="boxetser">
                     <span>1,321</span>
                     <div class="boxserter">
                        <span class="quartercolor"></span>
                        <span class="quartertitle">销售额(万元)</span>
                     </div>
                  </div>
               </div>
            </div>
         </div>
         <!-- 排行-->
         <div class="top panel">
            <div class="lefttop">
               <h3>全国热榜</h3>
               <ul class="lefttopul">
                  <li>
                     <img src="@/assets/images/one.webp" alt="" class="headimg">
                     <span>可爱多</span>
                  </li>
                  <li>
                     <img src="@/assets/images/one.webp" alt="" class="headimg">
                     <span>可爱多</span>
                  </li>
                  <li>
                     <img src="@/assets/images/one.webp" alt="" class="headimg">
                     <span>可爱多</span>
                  </li>
               </ul>
            </div>
            <div class="righttop">
               <h3>各省热销</h3>
               <div class="righttopul">
                  <ul class="sup">
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>

                  </ul>
                  <ul class="sup">
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>
                     <li>
                        <span>北京</span>
                        <div>
                           <span>21.023</span>
                           <div class="sopspan"></div>
                        </div>
                     </li>

                  </ul>
               </div>
            </div>
         </div>
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

      background-color: red;
   }

   .user {
      height: 1.7708rem;
   }
}
</style>
