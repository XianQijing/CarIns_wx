<template>
  <div class="Card">
    <div class="alluse">
      <p style="margin-bottom:0.1rem;">保单信息</p>
      <div>
        <p>商业险：</p>
        <p>￥30000</p>
      </div>
      <div>
        <p>车辆损失保险：</p>
        <p>￥1245.00</p>
      </div>
      <div>
        <p>第三者责任险：</p>
        <p>￥1743.00</p>
      </div>
      <div>
        <p>不计免赔：</p>
        <p>￥91.30</p>
      </div>
      <div>
        <p>车船税：</p>
        <p>￥91.30</p>
      </div>
      <div>
        <p>交强险：</p>
        <p>￥91.30</p>
      </div>
      <div>
        <!-- <p>不计免赔</p> -->
        <p style="text-align: right;width: 100%;">实付金额：￥91.30</p>
      </div>
    </div>
    <div style="position: absolute;bottom: 0.16rem; width:100%">
      <div class="btnn">
        <button @click="$router.push({name: 'Pay'})">立即投保</button>
        <button @click="$router.push({name: 'HelloWorld'})">分期投保</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card'
}
</script>

<style lang="less" scoped>
.Card {
  background: #f2f2f2;
  height: 100%;
  box-sizing: border-box;
  padding-top: 0.1rem;
  position: relative;
  .btnn {
    width: 90%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    button {
      width: 1.33rem;
      height: 0.49rem;
      color: white;
      border-radius: 0.1rem;
      border: none;
      background: #4B86FE;
    }
  }
  .alluse {
    div {
      p:nth-child(1){
        color: #666666;
      }
    }
  }
}
</style>
