<template>
  <div class="chart" ref="column_con"></div>
</template>

<script>
export default  {
  props:{
    vdata:{
      type:Object,
      default:()=>({
        data:[
          [
            { value: 231, name: '男' },
            { value: 1048, name: '女' },
          ],
          [
            { value: 231, name: '60-69岁' },
            { value: 1048, name: '70-79岁' },
            { value: 1048, name: '80-89岁' },
            { value: 1048, name: '90-99岁' },
            { value: 1048, name: '100岁及以上' },
          ],
        ],
      })
    },
  },
  mounted() {
    this.getInstance();
  },
  methods: {
    // 实例化对象 进行图形化渲染
    getInstance() {
      const { Pie, Basis } = this.$mychar;

      let option = new Pie().renderMultiPie(this.vdata);

      this.custom(option);

      Basis.render(this.$refs.column_con, option);
    },

    // 自定义配置
    custom(option){
      option.legend.textStyle.color = '#fff';
      option.legend.right = '15%';
    }
  },

  watch:{
    vdata:{
      handler(){
        this.getInstance()
      },
      deep: true
    }
  }
}
</script>

<style scoped>
  .chart{
    width: 100%;
    height: 100%;
  }
</style>