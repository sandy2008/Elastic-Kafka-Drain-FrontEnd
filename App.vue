

<template>
  <div id="app">
    <header class="header">
        <el-row>
            <el-col :span="24">
              <el-menu default-active="5" class="el-menu-demo" mode="horizontal">
                <el-menu-item index="1">Starter</el-menu-item>
                <el-menu-item index="2">Controller</el-menu-item>
                <el-menu-item index="3">Settings</el-menu-item>
                <el-menu-item index="4">Help</el-menu-item>
                <el-menu-item index="5">About</el-menu-item>
              </el-menu>
            </el-col>
        </el-row>
        </header>
    
    <main>
              <!-- 左侧导航 -->
            <div class="main-left">
              <el-menu default-active="/activePublic" class="el-menu-vertical-demo" :router="true">
                <el-menu-item index="/activePublic" :class="{'isActive': active}">Easy Setup</el-menu-item>
                <el-menu-item index="/activeManage" :class="{'isActive': !active}">Complete</el-menu-item>
              </el-menu>
            </div>

              <!-- 右侧主内容区 -->
              <div  class="main-right" >
              <div>
                <el-input placeholder="0000,0001,0002" v-model="input3">
                  <template slot="prepend">Topic</template>
                </el-input>
              </div>
              <div style="margin-top: 15px;">
                <el-input placeholder="0,1,2,3,4,5" v-model="input3">
                  <template slot="prepend">Partition</template>
                </el-input>
              </div>
              <div style="margin-top: 15px;">
                <el-input placeholder="127.0.0.1" v-model="input3">
                  <template slot="prepend">Brokers</template>
                </el-input>
              </div>
              <div style="margin-top: 15px;">
                <el-input placeholder="127.0.0.1:9200" v-model="input3">
                  <template slot="prepend">Elastic Address</template>
                </el-input>
              </div>
              <div style="margin-top: 15px;">
                Drain Number :
              <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10" label="number">
              </el-input-number>
              </div>
               <div style="margin-top: 15px;">
                <el-date-picker
                  v-model="value4"
                  type="datetimerange"
                  range-separator="To"
                  start-placeholder="Start Datetime"
                  end-placeholder="End Datetime">
                </el-date-picker>
                <el-button @click="startHacking">Start</el-button>
              </div>
                
              </div>
        </main>



  </div>
  
</template>

<script>
export default {
  data() {
    return {
      input: ''
    }
  }
}
</script>

<script>
  export default {
    data() {
      return {
        pickerOptions2: {
          shortcuts: [{
            text: '最近一周',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近一个月',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近三个月',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
              picker.$emit('pick', [start, end]);
            }
          }]
        },
        value4: [new Date(2000, 10, 10, 10, 10), new Date(2000, 10, 11, 10, 10)],
        value5: ''
      };
    }
  };  
</script>

<style>
      body{margin: 0;}
    #app {
      min-width: 1200px;
      margin: 0 auto;
      font-family: "Helvetica Neue","PingFang SC",Arial,sans-serif;
    }
    /* 头部导航 */
    header{z-index: 1000;min-width: 1200px;transition: all 0.5s ease;  border-top: solid 4px #3091F2;  background-color: #fff;  box-shadow: 0 2px 4px 0 rgba(0,0,0,.12),0 0 6px 0 rgba(0,0,0,.04);  }
    header.header-fixed{position: fixed;top: 0;left: 0;right: 0;}
    header .el-menu-demo{padding-left: 300px!important;}

    /* 主内容区 */
      main{    display: -webkit-box;  display: -ms-flexbox;  display: flex;  min-height: 800px;  border: solid 40px #E9ECF1;  background-color: #FCFCFC;  }
      main .main-left{text-align: center;width: 200px;float: left;}
      main .main-right{-webkit-box-flex: 1;  -ms-flex: 1;  flex: 1;  background-color: #fff; padding: 50px 70px; }
      main .el-menu{background-color: transparent!important;}
    </style>

