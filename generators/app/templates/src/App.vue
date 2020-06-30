<template>
  <div id="app">
    <router-view/>
  </div>
</template>
<script>
export default{
  name: 'App',
  data() {
    return {
      timer: null,
      nowDate: new Date().getTime(), // 当前时间
      // timeOut: 120 * 60 * 1000, // 超时时间2小时
      timeOut: 120 * 60 * 1000, // 超时时间2小时
      whiteList: ['/login']
    }
  },
  created() {
    // 监听键盘，实现回车键控制按钮
    // document.addEventListener('mousemove', this.keyEnter)
    // document.addEventListener('keydown', this.keyEnter)
  },
  beforeDestroy() {
    // 销毁监听事件
    // document.removeEventListener('mousemove', this.keyEnter)
    // document.removeEventListener('keydown', this.keyEnter)
    // // 清除定时器
    // this.timer && clearInterval(this.timer)
  },
  mounted() {
    // this.timer && clearInterval(this.timer)
    // this.timer = setInterval(this.countDown, 1000)
  },
  methods: {
    keyEnter() {
      // 获取当前时间
      this.nowDate = new Date().getTime()
    },
    countDown() {
      const lastDate = new Date().getTime()
      const differ = lastDate - this.nowDate
      if (differ > this.timeOut) {
        // 退出登录
        this.$store.dispatch('LogOut').then(() => {
          if (this.whiteList.indexOf(this.$route.path) === -1) {
            // 清除定时器
            this.timer && clearInterval(this.timer)
            this.$alert('2小时未操作,请重新登录', '友情提示', {
              confirmButtonText: '重新登录',
              showClose: false,
              callback: action => {
                // 重启定时器
                this.timer = setInterval(this.countDown, 1000)
                this.$router.replace('/login')
              }
            })
          }
        })
      }
    }
  }
}
</script>
<style>
/* 解决table有border的时候，对不齐问题 */
  body .el-table th.gutter{
    display: table-cell!important;
  }
/* 解决错误信息过长时，toast超出屏幕宽度问题*/
  .el-message--error{
    max-width: 800px;
    word-break: break-all;
  }
  /* 解決table抖动问题 */
/*.el-table{*/
  /*width:99.9% !important;*/
/*}*/
</style>

