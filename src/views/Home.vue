<template>
  <div class="home">
     <div class="banner">

      <img class="hidden-xs-only hidden-sm-only hidden-md-only" :src="bannerLGXL" alt="banner 图"@click="open">
    </div>
    <!-- 第一行 -->
    <el-row>
      <el-col :xs="24" :sm="24" :md="24" :lg="6"  class="part">
        <PartOne></PartOne>
      </el-col>
      <el-col :xs="24" :sm="24" :md="12" :lg="12"  class="part">
        <PartTwo ref="two"></PartTwo>
      </el-col>
      <el-col :xs="24" :sm="24" :md="12" :lg="6"  class="part">
        <PartThree ref='three'></PartThree>
      </el-col>
    </el-row>
    <!-- 第二行 -->
    <el-row>
      <el-col :xs="24" :sm="24" :md="8" :lg="8" :xl="8" class="part" >
        <PartFour ref="four":option='option'></PartFour>
      </el-col>
      <el-col :xs="24" :sm="24" :md="8" :lg="8" :xl="8" class="part">
       	<PartFive></PartFive>
      </el-col>
      <el-col :xs="24" :sm="24" :md="4" :lg="4" :xl="4" class="part">
        <PartSix></PartSix>
      </el-col>
      <el-col :xs="24" :sm="24" :md="4" :lg="4" :xl="4" class="part">
        <PartSeven></PartSeven>
      </el-col>
    </el-row>
      <el-card style="width: 80%;margin:30px auto;background-color: #333;">
      <el-table
    :data="tableData"
    :default-sort = "{prop: 'date', order: 'descending'}"
    >
    <el-table-column
      prop="date"
      label="日期"
      sortable
      width="180"
      align="center">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      sortable
      align="center"
      >
    </el-table-column>
    <el-table-column
      prop="address"
      label="地址"
      :formatter="formatter"
      align="center">
       <template slot-scope="scope">
        <el-popover trigger="hover" placement="top">
          <p>姓名: {{ scope.row.name }}</p>
          <p>住址: {{ scope.row.address }}</p>
          <div slot="reference" class="name-wrapper">
            {{ scope.row.address }}
          </div>
        </el-popover>
      </template>
    </el-table-column>
    <el-table-column label="操作"      width="200" align="center">
      <template slot-scope="scope">
        <el-button
          
          @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
        <el-button
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>
  </el-card>
  </div>
</template>

<script>
// @ is an alias to /src
import PartOne from '@/components/PartOne.vue'
import PartTwo from '@/components/PartTwo.vue'
import PartThree from '@/components/PartThree.vue'
import PartFour from '@/components/PartFour.vue'
import PartFive from '@/components/PartFive.vue'
import PartSix from '@/components/PartSix.vue'
import PartSeven from '@/components/PartSeven.vue'

export default {
  name: 'home',
  data() {
    return {
      tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }],
      bannerXSSM: require("../assets/img/banner_640.png"),
      bannerMD: require("../assets/img/banner_1000.png"),
      bannerLGXL: require("../assets/img/banner.png"),
      option: {
                 // 标题
        title: {
          // 标题文本
          text: "文章成就统计",
          // 标题文本样式
          textStyle: {
            color: "#fff"
          },
          // 标题位置
          x: "center"
        },
        // 图形布局
        grid: {
          // 距离底部高度
          bottom: "20"
        },
        // 横轴
        xAxis: {
          show: false,
          type: "category",
          data: ["Github 提交：\n1141", "Github Star数：\n269", "掘金点赞量：\n1508", "掘金关注者：\n234"],
          axisLine: {
            lineStyle: {
              color: "#fff"
            }
          },
          axisLabel: {
            // 横轴信息全部显示
            interval: 0
          }
        },
        // 纵轴
        yAxis: {
          type: "value",
          axisLine: {
            lineStyle: {
              color: "#fff"
            }
          },
          axisLabel: {
            // 横轴信息全部显示
            interval: 0
          }
        },
        // 图形系列
        series: [
          {
            // 图类型
            type: "bar",
            // 数据
            data: [1141, 269, 1508, 234],
            // 文本
            label: {
              show: true,
              position: "top",
              color: "#fff",
              formatter: "{b}"
            },
            // 柱条样式
            itemStyle: {
              color: "deepskyblue"
            },
            zlevel: 1
          }
        ]

            }
    };
  },
  components: {
    PartOne,
    PartTwo,
    PartThree,
    PartFour,
    PartFive,
    PartSix,
    PartSeven,
  },
    mounted() {
      var mains = document.getElementsByClassName('home');
//返回一个伪数组
for (var i = 0; i < mains.length; i++) {
  var main = mains[i];
  console.log('main',main);
}
    var two=this.$refs.two.gettwo();
    var three=this.$refs.three.getthree();
    var four=this.$refs.four.getfour();
    window.onresize = function(){
      three.resize();
      two.resize();    //若有多个图表变动，可多写
      four.resize();
    }

  },
  created(){
 
  },
  methods: {
        open() {
            console.log(this.option.series)
            this.$message('这是一条消息提示');
      this.option.xAxis.data = ["Github 提交：\n1200", "Github Star数：\n810", "掘金点赞量：\n1610", "掘金关注者：\n401"]
    this.option.series[0].data = [1200, 810, 1610, 401 ]
            this.$refs.four.drawECharts()
            console.log(111,)          
        },
         formatter(row, column) {
        return row.address;
      },
            handleEdit(index, row) {
        console.log(index, row);
      },
      handleDelete(index, row) {
        console.log(index, row);
      }

    }
}
</script>
