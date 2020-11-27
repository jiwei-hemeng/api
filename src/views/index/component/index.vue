<template>
  <div class="Detail">
    <el-page-header :content="title" @back="goBack"></el-page-header>
    <div class="content">
      <!-- <DetailItem /> -->
      <el-tabs tab-position="left">
        <el-tab-pane label="对接过程">
          <div>
            <Butt :id="id" />
          </div>
        </el-tab-pane>
        <el-tab-pane label="接口说明">
          <el-tabs>
            <el-tab-pane label="API使用说明">
              <UseExplain :id="id" />
            </el-tab-pane>
            <el-tab-pane label="错误码参照">
              <ErrCode :id="id" />
            </el-tab-pane>
            <el-tab-pane label="示例代码">
              <span>java 示例</span>
              <JAVACode :id="id" />
              <span>C# 示例</span>
              <CCode :id="id" />
            </el-tab-pane>
            <el-tab-pane label="API参数说明">
              <Arguments :id="id" />
            </el-tab-pane>
            <el-tab-pane label="版本信息">
              <version :id="id" />
            </el-tab-pane>
            <el-tab-pane label="系统信息">
              <xt :id="id" />
            </el-tab-pane>
          </el-tabs>
        </el-tab-pane>
        <el-tab-pane label="对接说明">
          <!-- 测试准备对接正式对接 -->
          <el-tabs>
            <el-tab-pane label="测试">
              <Test :id="id" />
            </el-tab-pane>
            <el-tab-pane label="准备对接">
              <Prepare :id="id" />
            </el-tab-pane>
            <el-tab-pane label="正式对接">
              <Accomplish :id="id" />
            </el-tab-pane>
          </el-tabs>
        </el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>
<script>
  import Butt from './List/butt'
  import UseExplain from './List/useExplain/'
  import Arguments from './List/arguments'
  import ErrCode from './List/errCode'
  import JAVACode from './List/javaCode'
  import CCode from './List/cCode'
  import version from './List/version'
  import xt from './List/xt_Info'
  import Test from './List/test'
  import Prepare from './List/prepare'
  import Accomplish from './List/accomplish'
  export default {
    name: 'Detail',
    components: {
      Butt,
      UseExplain,
      Arguments,
      ErrCode,
      JAVACode,
      CCode,
      version,
      xt,
      Test,
      Prepare,
      Accomplish,
    },
    props: {
      id: {
        type: Number,
        required: true,
      },
      title: {
        type: String,
        required: true,
      },
    },
    data() {
      return {
        // imgArr: [{ id: 1, src: require('./List/sd_01/1.png') }],
      }
    },
    created() {},
    mounted() {},
    methods: {
      goBack() {
        this.$emit('close')
      },
    },
  }
</script>
<style scoped>
  .content {
    box-sizing: border-box;
    padding: 10px;
  }
  /deep/ .el-tabs__header.is-left {
    padding-top: 60px;
  }
</style>
