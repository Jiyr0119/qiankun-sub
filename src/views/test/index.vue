<template>
  <div class="wrapper">
    <h1>您好，欢迎您进入微应用{{ url }}的页面</h1>
    <el-transfer
      v-if="pathName === '/microApp'"
      v-model="value"
      filterable
      :filter-method="filterMethod"
      filter-placeholder="请输入城市拼音"
      :data="data"
    />
    <el-form v-else ref="form" :model="form" label-width="80px">
      <el-form-item label="活动名称">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="活动区域">
        <el-select v-model="form.region" placeholder="请选择活动区域">
          <el-option label="区域一" value="shanghai" />
          <el-option label="区域二" value="beijing" />
        </el-select>
      </el-form-item>
      <el-form-item label="活动时间">
        <el-col :span="11">
          <el-date-picker
            v-model="form.date1"
            type="date"
            placeholder="选择日期"
            style="width: 100%;"
          />
        </el-col>
        <el-col class="line" :span="2">-</el-col>
        <el-col :span="11">
          <el-time-picker
            v-model="form.date2"
            placeholder="选择时间"
            style="width: 100%;"
          />
        </el-col>
      </el-form-item>
      <el-form-item label="即时配送">
        <el-switch v-model="form.delivery" />
      </el-form-item>
      <el-form-item label="活动性质">
        <el-checkbox-group v-model="form.type">
          <el-checkbox label="美食/餐厅线上活动" name="type" />
          <el-checkbox label="地推活动" name="type" />
          <el-checkbox label="线下主题活动" name="type" />
          <el-checkbox label="单纯品牌曝光" name="type" />
        </el-checkbox-group>
      </el-form-item>
      <el-form-item label="特殊资源">
        <el-radio-group v-model="form.resource">
          <el-radio label="线上品牌商赞助" />
          <el-radio label="线下场地免费" />
        </el-radio-group>
      </el-form-item>
      <el-form-item label="活动形式">
        <el-input v-model="form.desc" type="textarea" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">立即创建</el-button>
        <el-button>取消</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    const generateData = _ => {
      const data = []
      const cities = ['上海', '北京', '广州', '深圳', '南京', '西安', '成都']
      const pinyin = [
        'shanghai',
        'beijing',
        'guangzhou',
        'shenzhen',
        'nanjing',
        'xian',
        'chengdu'
      ]
      cities.forEach((city, index) => {
        data.push({
          label: city,
          key: index,
          pinyin: pinyin[index]
        })
      })
      return data
    }
    return {
      url: window.location.href,
      pathName: window.location.pathname,
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      },
      data: generateData(),
      value: [],
      filterMethod(query, item) {
        return item.pinyin.indexOf(query) > -1
      }
    }
  },
  computed: {},
  watch: {},
  created() {
    console.log(window.location)
  },
  mounted() {},
  methods: {
    onSubmit() {
      console.log('submit!')
    }
  }
}
</script>
<style scoped lang="scss">
.wrapper {
  padding: 20px;
}
/* @import url(); 引入公共css类 */
</style>
