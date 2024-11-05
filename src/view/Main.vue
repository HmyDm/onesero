<template>
  <el-container style="height: 100vh; width: 100%; background-color: #27265c;">
    <el-aside width="190px" style="background-color: #27265c">
      <!-- 侧边栏 -->
      <el-col>
        <el-menu default-active="1" class="el-menu-vertical-demo" background-color="#27265c" text-color="#fff"
          active-text-color="#ffd04b">
          <img src="../assets/image/logo.png" style="width: 197px; height: 61px;" />
          <el-menu-item index="1">
            <i class="iconfont">&#xe602;</i>&nbsp;
            <span slot="title">首页</span>
          </el-menu-item>
          <el-menu-item index="2">
            <i class="iconfont">&#xe995;</i>&nbsp;
            <span slot="title">电力监控</span>
          </el-menu-item>
          <el-menu-item index="3">
            <i class="iconfont">&#xe964;</i>&nbsp;
            <span slot="title">光伏区监控</span>
          </el-menu-item>
          <el-menu-item index="4">
            <i class="iconfont">&#xeb91;</i>&nbsp;
            <span slot="title">设备分布图</span>
          </el-menu-item>
          <el-menu-item index="5">
            <i class="iconfont">&#xe8bf;</i>&nbsp;
            <span slot="title">设备实时数据</span>
          </el-menu-item>
          <el-menu-item index="6">
            <i class="iconfont">&#xe621;</i>&nbsp;
            <span slot="title">故障告警</span>
          </el-menu-item>
          <el-menu-item index="7">
            <i class="iconfont">&#xe6d5;</i>&nbsp;
            <span slot="title">运程控制</span>
          </el-menu-item>
        </el-menu>
      </el-col>
    </el-aside>

    <el-container>
      <!-- 顶栏 -->
      <el-header>
        <el-menu class="el-menu-demo" mode="horizontal" background-color="#363568" text-color="#fff"
          active-text-color="#ffd04b" style="height: 60px; width: 100%;">
          <el-menu-item index="1"> <router-link to="/main">
              <i class="iconfont">&#xf00a7;</i> &nbsp;运行程序</router-link></el-menu-item>
          <el-menu-item index="2"><i class="iconfont">&#xe613;</i> &nbsp;生产管理</el-menu-item>
          <el-menu-item index="3"><i class="iconfont">&#xe62e;</i> &nbsp;电站维护</el-menu-item>
          <el-menu-item index="4"><i class="el-icon-setting"></i>系统管理</el-menu-item>
          <!-- 右边 -->
          <div class="topRight">
            <span>{{currentTime }} &nbsp;| &nbsp;{{date}}</span>&nbsp;&nbsp;&nbsp;
            <img src="../assets/image/tou.jpg" alt="我的头像" title="自定义头像" class="avatar">&nbsp;
            <el-dropdown>
              <span class="el-dropdown-link">
                {{name}}<i class="el-icon-arrow-down el-icon--right"></i>
              </span>
              <el-dropdown-menu slot="dropdown">
                <el-dropdown-item icon="el-icon-s-custom">个人中心</el-dropdown-item>
                <el-dropdown-item icon="el-icon-circle-plus">切换用户</el-dropdown-item>
                <el-dropdown-item icon="el-icon-switch-button">退出登录</el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
            <i class="iconfont2 " title="讨论">&#xe60e;</i>
            <i class="iconfont2 " title="帮助">&#xe8ac;</i>
            <i class="iconfont2 " title="退出系统">&#xe62c;</i>
          </div>
        </el-menu>
      </el-header>
      <!-- 首页主体 -->
      <el-main>
        <!-- 创建响应式布局 -->
        <el-row :gutter="20">
          <!-- 发电与功率卡片 -->
          <el-col :xs="24" :sm="12" :md="8" :lg="8" :xl="8">
            <div class="cardOne">
              <div class="title">
                <h2 class="text"> &nbsp; &nbsp;<i class="iconfont">&#xe60f; </i>&nbsp;发电与功率</h2>
              </div>
              <!-- 卡1 -->
              <div class="progress">
                <div class="left1">
                  <img src="../assets/image/累计发电.png" alt="累计发电" class="imgu">
                </div>
                <div class="right1">
                  <span class="listOne-left">累计发电</span>
                  <span class="listOne-right"><span style="color: #f5e441; font-size: 22px;">123589256.00</span>
                    kWh</span>
                  <div class="g-container">
                    <div class="g-progress1"></div>
                  </div>
                </div>
              </div>
              <!-- 卡2 -->
              <div class="progress">
                <div class="left1">
                  <img src="../assets/image/今日发电.png" alt="累计发电" class="imgu">
                </div>
                <div class="right1">
                  <span class="listOne-left">今日发电</span>
                  <span class="listOne-right"><span style="color: #01caf8; font-size: 22px;">4567.00</span>
                    kWh</span>
                  <div class="g-container">
                    <div class="g-progress2"></div>
                  </div>
                </div>
              </div>
              <!-- 卡3 -->
              <div class="progress">
                <div class="left1">
                  <img src="../assets/image/当日.png" alt="累计发电" class="imgu">
                </div>
                <div class="right1">
                  <span class="listOne-left">当前功率</span>
                  <span class="listOne-right"><span style="color: #d52af8; font-size: 22px;">567.00</span>
                    kWh</span>
                  <div class="g-container">
                    <div class="g-progress3"></div>
                  </div>
                </div>
              </div>
            </div>
          </el-col>
          <!-- 节能减排卡片 -->
          <el-col :xs="24" :sm="12" :md="8" :lg="8" :xl="8">
            <div class="cardTwo">
              <!-- 卡片内容 -->
              <div class="title">
                <h2> &nbsp; &nbsp;<i class="iconfont">&#xe666;</i> &nbsp;节能减排</h2>
              </div>
              <ul class="list-color1">
                <li v-for="detail in saveEnergy " :key="detail.id">
                  <img :src="detail.imageUrl" style="vertical-align: middle;">&nbsp;&nbsp;
                  {{detail.label}}<span
                    class="right"><strong>{{detail.value}}</strong>&nbsp;&nbsp;{{detail.unit}}</span>
                </li>
              </ul>
            </div>
          </el-col>
          <!-- 电站基本信息卡片 -->
          <el-col :xs="24" :sm="12" :md="8" :lg="8" :xl="8">
            <div class="cardThree">
              <!-- 卡片内容 -->
              <div class="title">
                <h2> &nbsp; &nbsp;<i class="iconfont">&#xeb66;</i> &nbsp;电站基本信息</h2>
              </div>
              <div>
                <ul class="list-color2">
                  <li v-for="detail in Details" :key="detail.id">
                    {{detail.label}}<span class="right">{{detail.value}}</span>
                  </li>
                </ul>
              </div>
            </div>
          </el-col>
        </el-row>
        <el-row :gutter="20">
          <el-col :xs="24" :sm="12" :md="5" :lg="12" :xl="12">
            <div class="cardFour">
              <div class="title">
                <h2>&nbsp; &nbsp;<i class="iconfont">&#xe7b5;</i> &nbsp;日功率-辐射强度</h2>
                <div id="title-sun">
                  <div class="icon1"></div>
                  <span class="icon-text">辐射强度</span>
                  <div class="icon2"></div>
                  <span class="icon-text">实时功率</span>
                  <a href="#" class="ahref"><i class="iconfont">&#xe84f;</i></a>
                </div>
              </div>
              <div ref="mychart" class="chartCentered">
              </div>
            </div>
          </el-col>
          <el-col :xs="24" :sm="12" :md="5" :lg="12" :xl="12">
            <div class="cardFour">
              <div class="title">
                <h2>&nbsp; &nbsp;<i class="iconfont">&#xe9d2;</i> &nbsp;日累计发电量</h2>
                <div id="title-sun">
                  <div class="icon1"></div>
                  <span class="icon-text">辐射强度</span>
                  <div class="icon2"></div>
                  <span class="icon-text">实时功率</span>
                  <a href="#" class="ahref"><i class="iconfont">&#xe84f;</i></a>
                </div>
              </div>
              <div ref="mychart2" class="chartCentered">
              </div>
            </div>
          </el-col>
        </el-row>
      </el-main>
    </el-container>

  </el-container>
</template>

<script>
  import * as echarts from "echarts";
  export default {
    name: 'Main',
    data() {
      return {
        currentTime: this.getCurrentTime(),
        date: '2018-07-26',
        name: '某某某',
        n1: '三十岗电站',
        Details: [{
            label: '电站名称',
            value: '三十岗电站'
          },
          {
            label: '经度/纬度',
            value: '东京117° 北纬23°'
          },
          {
            label: '装机功率',
            value: '123.23KW'
          },
          {
            label: '组件数量',
            value: '2000块'
          },
          {
            label: '电站类型',
            value: '分布式电站'
          },
          {
            label: '投运时间',
            value: '2018年06月10日'
          },
          {
            label: '生命周期',
            value: '25年'
          },
        ],
        saveEnergy: [{
            imageUrl: require('../assets/image/二氧化碳.png'),
            label: '二氧化碳',
            value: '8.45',
            unit: '万吨'
          },
          {
            imageUrl: require('../assets/image/汽车里程.png'),
            label: ' 汽车里程',
            value: '7.37',
            unit: 'KM'
          },
          {
            imageUrl: require('../assets/image/植树.png'),
            label: '等效增树',
            value: '461.79',
            unit: '万吨'
          },
          {
            imageUrl: require('../assets/image/二氧化硫.png'),
            label: '二氧化硫',
            value: '2542.91',
            unit: '吨'
          }
        ]
      }
    },
    methods: {
      // 获取当前时间
      getCurrentTime() {
        const now = new Date();
        const hours = now.getHours().toString().padStart(2, '0');
        const minutes = now.getMinutes().toString().padStart(2, '0');
        return `${hours}:${minutes}`;
      },
      // 更新时间
      updateTime() {
        this.currentTime = this.getCurrentTime();
      },

      // 图表
      initEcharts1() {
        const option1 = {
          tooltip: {
            trigger: 'axis'
          },
          xAxis: {
            type: 'category',
            boundaryGap: false,
            data: ["3", "6", "9", "12", "15", "18", "21", "24"]
          },
          yAxis: {
            type: 'value',
            splitLine: {
              lineStyle: {
                color: '#252458'
              }
            },
          },
          series: [{
              name: "实时功率",
              type: "line",
              smooth: true,
              showSymbol: false,
              lineStyle: {
                width: 0
              },
              data: [600, 1000, 1600, 1200, 800, 1600, 1000, 700],
              areaStyle: {
                opacity: 0.6,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#ab28d1'
                  },
                  {
                    offset: 1,
                    color: '#7d1d9d'
                  }
                ])
              },
            },
            {
              name: "辐射强度",
              type: "line",
              smooth: true,
              showSymbol: false,
              lineStyle: {
                width: 0
              },
              data: [500, 900, 900, 1200, 1600, 800, 1400, 700],
              areaStyle: {
                opacity: 0.8,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#0aadc2'
                  },
                  {
                    offset: 1,
                    color: '#343487',
                  }
                ])
              },
            },
          ],
        };
        // 左边的图表
        const myChart1 = echarts.init(this.$refs.mychart); // 图表初始化
        myChart1.setOption(option1); // 渲染页面
        // 自适应屏幕
        window.addEventListener("resize", function() {
          myChart1.resize();
        });
      },
      initEcharts2() {
        const option2 = {
          tooltip: {
            trigger: 'axis'
          },

          xAxis: {
            type: 'category',
            data: ["3", "6", "9", "12", "15", "18", "21", "24"],

          },

          yAxis: {
            type: 'value',
            splitLine: {
              lineStyle: {
                color: '#252458'
              }
            },
          },
          series: [{
              name: "辐射强度",
              type: "bar", //类型为柱状图
              showSymbol: false,
              barWidth: '15px',
              data: [600, 1000, 1600, 1200, 2000, 1500, 2000, 700],
              itemStyle: {
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#06fdff'
                  },
                  {
                    offset: 1,
                    color: '#472dbd'
                  }
                ])
              },
            },
            {
              name: "实时功率",
              type: "bar", //类型为柱状图
              showSymbol: false,
              barWidth: '15px',
              data: [500, 900, 900, 1200, 1600, 800, 1400, 700],
              itemStyle: {
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#e53cff'
                  },
                  {
                    offset: 1,
                    color: '#573bc3'
                  }
                ])
              },
            },
          ],
        };
        // 左边的图表
        const myChart2 = echarts.init(this.$refs.mychart2); // 图表初始化
        myChart2.setOption(option2); // 渲染页面
        // 自适应屏幕
        window.addEventListener("resize", function() {
          myChart2.resize();
        });
      },

    },
    mounted() {
      // 每分钟更新时间
      setInterval(this.updateTime, 60000);
      this.initEcharts1();
      this.initEcharts2();
    },
  }
</script>

<style>
  @import '../assets/css/main.css';
</style>
