<template>
  <div class="dash">
    <div class="dashRow">
      <el-card class="dashRowItem" shadow="always">
        <p class="dashRowItemKey">S</p>
        <p class="dashRowItemTitle">食品安全案列</p>
        {{createData}}
      </el-card>
      <el-card class="dashRowItem" shadow="always">
        <p class="dashRowItemKey">A</p>
        <p class="dashRowItemTitle">企业黑名单数</p>
        {{retreiveData}}
      </el-card>
      <el-card class="dashRowItem" shadow="always">
        <p class="dashRowItemKey">F</p>
        <p class="dashRowItemTitle">前七天访问数</p>
        {{updateData}}
      </el-card>
      <el-card class="dashRowItem" shadow="always">
        <p class="dashRowItemKey">E</p>
        <p class="dashRowItemTitle">食品安全新闻</p>
        {{deleteData}} 
      </el-card>
    
    </div>

    <div class="dashRow">
      <div class="dashRowMiddle">
        <line-chart></line-chart>
      </div>
    </div>

    <div class="dashRow">
      <div class="dashRowGraph">
        <bar-chart></bar-chart>
      </div>
      <!-- <div class="dashRowGraph">
        <radar-chart></radar-chart>
      </div> -->
      <div class="dashRowGraph">
        <pie-chart></pie-chart>
      </div>
      <!-- <div class="dashRowGraph">
        <bar-chart></bar-chart>
      </div> -->
    </div>

    <!-- <div class="dashRow">
      <swiper-img class="dashRowSwiper"></swiper-img>
      <todo-list class="dashRowTodo"></todo-list>
      <cool-clock class="dashRowClock"></cool-clock>
    </div> -->

    <!-- 空白占位，方便后续内容拓展，同时防止页面下方被hidden -->
    <div class="dashBlock"></div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import LineChart from './components/LineChart.vue'
import RadarChart from './components/RadarChart.vue'
import PieChart from './components/PieChart.vue'
import BarChart from './components/BarChart.vue'
import SwiperImg from './components/SwiperImg.vue'
import TodoList from './components/TodoList.vue'
import CoolClock from './components/CoolClock.vue'

@Component({
  components: { 
    LineChart,
    RadarChart,
    PieChart,
    BarChart,
    SwiperImg,
    TodoList,
    CoolClock
  }
})
export default class DashBoard extends Vue {
  createData: string = "1,000,0"
  retreiveData: string = "2,000"
  updateData: string = "500"
  deleteData: string = "1,000"
  chartLine: any
}
</script>

<style lang="less" scoped>
.dash {
  width: 100%;
  // border: 2px solid blue;
  // height: 100%;
  display: flex;
  flex-flow: column wrap;
  justify-content: space-around;
  align-items: center;
  margin: 30px auto;
  font-size: 1.5rem;

  &Row {
    width: 100%;
    margin-bottom: 40px;
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    align-items: center;
    // border: 2px solid red;

    &Item {
      width: 24%;
      text-align: left;
      line-height: 40px;
      border-radius: 10px;
      background-color:	white;
      box-shadow: 1px 1px 1px rgba(0,0,0,.3);
      border-color: rgba(0,0,0,.05);

      &Title {
        color: rgb(113, 125, 126)
      }

      &Key {
        width: 50px;
        height: 50px;
        float: right;
        color: rgba(100, 181, 246, 1);
        border-radius: 50px;
        text-align: center;
        line-height: 50px;
        border: 2px solid rgb(113, 125, 126);
        // -webkit-transform: rotate(-30deg); 
        transform: rotate(-30deg);
        transition: width 1s, height 1s;
        -moz-transition: width 1s, height 1s, -moz-transform 1s; /* Firefox 4 */
        -webkit-transition: width 1s, height 1s, -webkit-transform 1s; /* Safari and Chrome */
        -o-transition: width 1s, height 1s, -o-transform 1s; /* Opera */
        opacity: 0.5;
      }

      &Key:hover {
        width: 50px;
        height: 50px;
        transform:rotate(1080deg);
        -moz-transform:rotate(1080deg); /* Firefox 4 */
        -webkit-transform:rotate(1080deg); /* Safari and Chrome */
        -o-transform:rotate(1080deg); /* Opera */
        border-radius: 60px;
        line-height: 50px;
        color: rgb(123, 31, 162);
        border: 2px solid rgb(142, 68, 173 );
        opacity: 1;
      }
    }

    &Swiper {
      width: 35%;
      margin: 20px 0;
    }

    &Todo {
      width: 30%;
      margin: 20px 0;
    }

    &Clock {
      width: 30%;
      margin: 20px 0;
    }

    &Middle {
      width: 100%;
      background-color:	white;
      padding: 15px;
      box-shadow: 1px 1px 1px rgba(0,0,0,.3);
      border-color: rgba(0,0,0,.05);
    }

    &Graph {
      width: 47%;
      padding: 10px;
      background-color: white;
      box-shadow: 1px 1px 1px rgba(0,0,0,.3);
      border-color: rgba(0,0,0,.5);
    }

    @media screen and (max-width:1000px) {
      &Item {
        width: 100%;
        margin: 10px 0;
      }

      &Graph {
        width: 100%;
        margin: 2px;
      }

      &Swiper {
        width: 100%;
      }

      &Todo {
        width: 100%;
      }

      &Clock {
        width: 100%;
      }
    }
  }

  &Block {
    flex: 0 0 50px;
  }
}
</style>