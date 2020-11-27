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
            <el-tab-pane label="错误码参照">错误码参照</el-tab-pane>
            <el-tab-pane label="示例代码">示例代码</el-tab-pane>
            <el-tab-pane label="API参数说明">API参数说明</el-tab-pane>
            <el-tab-pane label="版本信息">版本信息</el-tab-pane>
            <el-tab-pane label="系统信息">系统信息</el-tab-pane>
          </el-tabs>
        </el-tab-pane>
        <el-tab-pane label="对接说明">
          <!-- 测试准备对接正式对接 -->
          <el-tabs>
            <el-tab-pane label="测试">测试</el-tab-pane>
            <el-tab-pane label="准备对接">准备对接</el-tab-pane>
            <el-tab-pane label="正式对接">正式对接</el-tab-pane>
          </el-tabs>
        </el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>
<script>
  import Butt from './List/butt'
  import UseExplain from './List/useExplain/'
  export default {
    name: 'Detail',
    components: {
      Butt,
      UseExplain,
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
