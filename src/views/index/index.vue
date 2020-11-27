<template>
  <div class="index">
    <el-row v-if="isDetail" class="box" type="flex" :gutter="10">
      <el-col v-for="(item, index) in sd_arr" :key="index" :span="6">
        <el-card shadow="hover">
          <div class="card" @click="toItem(item)">
            <el-image :src="img_obj[img_arr[index]]"></el-image>
            <p>{{ item.name }}</p>
          </div>
        </el-card>
      </el-col>
    </el-row>
    <div v-else>
      <Detail :id="select_id" :title="title" @close="isDetail = true" />
    </div>
  </div>
</template>

<script>
  const ctx = require.context('./images', false, /\.png$/)
  const map = {}
  for (const key of ctx.keys()) {
    map[key] = ctx(key)
  }
  import { getItem } from './images'
  import Detail from './component'
  export default {
    name: 'Index',
    components: {
      Detail,
    },
    data() {
      return {
        img_arr: ctx.keys(),
        img_obj: map,
        sd_arr: getItem(),
        select_id: 0,
        isDetail: true,
        title: '',
      }
    },
    beforeDestroy() {},
    mounted() {},
    methods: {
      toItem(item) {
        this.select_id = item.id
        this.title = item.name
        this.isDetail = false
      },
    },
  }
</script>
<style lang="scss" scoped>
  .index {
    box-sizing: border-box;
    padding: 10px;
    .box {
      flex-wrap: wrap;
      .card {
        min-height: 130px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
      }
    }
  }
</style>
