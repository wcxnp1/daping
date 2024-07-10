<script setup>
import { reactive } from 'vue'
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
// 数值的逗号
function addCommaToNumber (num) {
   return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
}
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
         <div class="monitor panel">交易详情</div>
         <!--  销售地分布统计-->
         <div class="point panel">销售地分布统计</div>
      </div>
      <!-- 第二列-->
      <div class="column">
         <!--  设备数据统计-->
         <div class="map">设备数据统计</div>
         <!--  用户总量统计-->
         <div class="user panel">用户总量统计</div>
      </div>
      <!-- 第三列-->
      <div class="column panel">
         <!-- 订单-->
         <div class="order panel">订单</div>
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

.column {
   flex: 3;

   .overview {
      height: .5729rem;
   }

   .panel {
      border-image: url("@/assets/images/border.png");
      border-image-width: .2604rem .3385rem .125rem .6979rem;
      border-image-slice: 56 44 39 140;
      position: relative;
      padding: .1042rem .1042rem;
      margin-bottom: .1042rem;


   }

   // .inner{
   //     position: absolute;

   // }
   .monitor {
      height: 2.5rem;
   }

   .point {
      height: 1.7708rem;
   }

   .order {
      height: .7813rem;
   }

   .sales {
      height: 1.2917rem;
   }

   .wrap {
      display: flex;

      .channel {
         flex: 1;
         height: 1.2083rem;
         margin-right: .1042rem;
      }

      .quarter {
         flex: 1;
         height: 1.2083rem;
      }
   }

   .top {
      height: 1.4583rem;
   }
}

.column:nth-child(2) {
   flex: 4;
   // margin: 30.217px 15.760px;

   .map {
      height: 3.0729rem;
      margin-bottom: .1042rem;
      // background: rgba(0,0,0,0.5);
      background-color: red;
   }

   .user {
      height: 1.7708rem;
   }
}
</style>
