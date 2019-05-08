<template>
  <div class="app-container">
    <!-- 通知和 计算股权与现金分红 -->
    <div class="partner-manage">
      <div class="notice">
        <ul>
          <li>通知</li>
          <li>更多</li>
        </ul>
      </div>
      <div class="compute"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      
    }
  },
  methods: {
    
  }
}
</script>

<style lang="scss" scoped>
  .app-container{
    width:100%;
    .partner-manage{
      width:100%;
      height:200px;
      display: flex;
      .notice{
        width:49%;
        height:200px;
        background:#e8edf3;
        padding:20px;
        box-sizing: border-box;
        ul{
          width:100%;
          height:40px;
          display: flex;
          justify-content: space-between;
        }
      }
      .compute{
        width:49%;
        margin-left:30px;
      }
    }
  }
</style>

