<template>
  <div class="arguments">
    <el-table :data="table_data_up" style="width: 100%">
      <el-table-column prop="submitName" label="字段名称"></el-table-column>
      <el-table-column prop="title" label="数据采集项"></el-table-column>
      <el-table-column prop="type" label="数据类型"></el-table-column>
      <el-table-column prop="notNull" label="上传时不能为空"></el-table-column>
      <el-table-column prop="example" label="举例"></el-table-column>
      <el-table-column prop="remark" label="备注"></el-table-column>
    </el-table>
    <div v-for="(item, index) in table_data_down" :key="index">
      <div class="table_header">{{ item.submitName }}</div>
      <table class="table">
        <tr v-for="(j, i) in item.list" :key="i">
          <td>{{ j.val }}</td>
          <td>{{ j.remark }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
  // API参数说明
  const ctx = require.context('../images', true, /\.json$/)
  const map = {}
  for (const key of ctx.keys()) {
    map[key] = ctx(key)
  }
  export default {
    name: 'Arguments',
    props: {
      id: {
        type: Number,
        require: true,
        default: 0,
      },
    },
    data() {
      return {
        // img_obj: {},
        // img_arr: [],
      }
    },
    computed: {
      table_data_up: function () {
        let arr = []
        const index = this.id - 1
        let obj = map[ctx.keys()[index]]
        arr = obj.object.up
        return arr
      },
      table_data_down: function () {
        let arr = []
        const index = this.id - 1
        let obj = map[ctx.keys()[index]]
        arr = obj.object.down
        return arr
      },
    },
    created() {
      console.log('table_data', this.table_data_up, this.table_data_down)
    },
    mounted() {},
    methods: {},
  }
</script>
<style scoped>
  .table_header {
    width: 100%;
    height: 40px;
    text-align: center;
    line-height: 40px;
  }
  .table {
    border-collapse: collapse;
    margin: 0 auto;
    width: calc(100% - 200px);
    text-align: center;
    border: 1px solid #483d8b;
  }
  table tr {
    height: 30px;
  }
  table tr:nth-child(odd) {
    background: #fff;
  }
  table tr:nth-child(even) {
    background: #f5fafa;
  }
</style>
