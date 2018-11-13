<template>
  <div class="aging">
    <div class="title">确认分期信息</div>
    <div class="msg">
      <van-cell-group>
        <van-cell title="姓名：" value="王麻麻" />
        <van-cell title="车牌号：" value="沪12345s" />
        <van-cell title="分期总金额：" value="6500 元" />
        <van-cell title="月付期数：" value="12期" />
        <button>分期详情</button>
      </van-cell-group>
    </div>
    <van-checkbox v-model="checked">我已阅读并同意《xxxx车险协议》</van-checkbox>
    <div class="btn">
      <van-button size="large" round @click="$router.push({name: 'Pay'})" >下一步</van-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Aging',
  data () {
    return {
      checked: true
    }
  }
}
</script>

<style lang="less" scoped>
.van-checkbox {
  font-size: 0.16rem;
  color: #666666;
  padding-left: 0.25rem;
  margin-top: 0.2rem;
}
.van-cell {
  padding: 0.13rem 0.15rem;
  color: #666;
}
.aging {
  background: #f2f2f2;
  height: calc(100% - 0.2rem);
  padding-top: 0.2rem;
  .title {
    font-size: 0.17rem;
    text-indent: 0.26rem;
    margin-bottom: 0.09rem;
  }
  .msg {
    width: 3.22rem;
    // height: 1.97rem;
    background:rgba(255,255,255,1);
    box-shadow:0px 1px 6px 1px rgba(206, 206, 206, 0.35);
    border-radius:10px;
    overflow: hidden;
    margin: 0 auto;
    position: relative;
    button {
      width: 0.84rem;
      height: 0.28rem;
      line-height: 0.28rem;
      background:rgba(75,134,254,1);
      border-radius:14px;
      border: 0;
      color: #fff;
      margin: 0.12rem 0.06rem;
      font-size: 0.14rem;
      float: right;
    }
  }
}
.btn {
  text-align: center;
  position: fixed;
  width: 100%;
  bottom: 0.1rem;
}
</style>
