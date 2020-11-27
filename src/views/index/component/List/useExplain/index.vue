<template>
  <div class="useExplain">
    <el-image :src="imgSrc"></el-image>
  </div>
</template>
<script>
  // API使用说明
  const ctx = require.context('../images', true, /2-1\.png$/)
  const map = {}
  for (const key of ctx.keys()) {
    map[key] = ctx(key)
  }
  export default {
    name: 'UseExplain',
    props: {
      id: {
        type: Number,
        require: true,
        default: 0,
      },
    },
    data() {
      return {
        img_obj: {},
        img_arr: [],
      }
    },
    computed: {
      imgSrc: function () {
        const index = this.id - 1
        let src = this.img_obj[this.img_arr[index]]
        return src
      },
    },
    created() {
      this.img_obj = map
      this.img_arr = ctx.keys()
    },
    mounted() {},
    methods: {},
  }
</script>
