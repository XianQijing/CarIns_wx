<template>
  <div class="driving">
    <div class="upload">
      <p>请上传行驶证内部照片</p>
      <div class="up">
        <div class="font box">
          <img src="../assets/img/driving.png" alt="">
          <!-- <div class="imgShow"></div> -->
          <input type="file" accept="image/*" @change="fileImage($event, 1)" capture="camera">
        </div>
      </div>
      <div class="span">本次收集的图片信息，仅作为此次投保使用</div>
    </div>

    <div style="margin-top: 0.03rem;">
      <van-cell-group style="padding: 0 0.25rem;">
        <div class="input">
          <div class="tit">
            车牌号:
          </div>
          <input type="text" placeholder="请输入车牌号">
        </div>
        <div class="input">
          <div class="tit">
            车架号:
          </div>
          <input type="text" placeholder="请输入车架号">
        </div>
        <div class="input">
          <div class="tit">
            初登日期:
          </div>
          <input type="text" placeholder="请输入初登日期">
        </div>
        <div class="input">
          <div class="tit">
            品牌型号:
          </div>
          <input type="text" placeholder="请输入品牌型号">
        </div>
      </van-cell-group>
    </div>

    <div class="owner">
      <p>车主信息</p>
      <div class="carOwner">
        <span>车主性质：</span>
        <van-radio-group v-model="radio">
          <van-radio name="1">私人</van-radio>
          <van-radio name="2">企业</van-radio>
          <van-radio name="2">机关</van-radio>
        </van-radio-group>
      </div>
      <div class="carOwner">
        <span>证件类型：</span>
        <span>身份证</span>
      </div>
    </div>

    <div class="cardUp">
      <div>
        <img src="../assets/img/font.png" alt="">
        <input accept="image/*"  type="file" @change="fileImage($event, 1)" capture="camera">
      </div>
      <div>
        <img src="../assets/img/back.png" alt="">
        <input accept="image/*"  type="file" @change="fileImage($event, 1)" capture="camera">
      </div>
    </div>

    <div style="margin-top: 0.03rem;">
      <van-cell-group style="padding: 0 0.25rem;">
        <div class="input">
          <div class="tit">
            证件号码:
          </div>
          <input type="text" placeholder="请输入证件号码">
        </div>
        <div class="input">
          <div class="tit">
            车主姓名:
          </div>
          <input type="text" placeholder="请输入车主姓名">
        </div>
        <div class="input">
          <div class="tit">
            手机号码:
          </div>
          <input type="text" placeholder="请输入手机号">
        </div>
      </van-cell-group>
    </div>

    <div class="owner">
      <p>其他投保信息</p>
      <div class="carOwner">
        <p>使用性质:</p>
        <van-radio-group v-model="radio">
          <van-radio name="1" style="width:0.9rem">非营业</van-radio>
          <van-radio name="2">营业</van-radio>
          <!-- <van-radio name="2">机关</van-radio> -->
        </van-radio-group>
      </div>
      <div class="carOwner">
        <p>投保人性质:</p>
        <van-radio-group v-model="radio">
          <van-radio name="1" style="width:0.9rem">个人</van-radio>
          <van-radio name="2">企业/机关</van-radio>
          <!-- <van-radio name="2">机关</van-radio> -->
        </van-radio-group>
      </div>
      <div class="carOwner">
        <p>是否过户:</p>
        <van-radio-group v-model="radio">
          <van-radio name="1" style="width:0.9rem">是</van-radio>
          <van-radio name="2">否</van-radio>
          <!-- <van-radio name="2">机关</van-radio> -->
        </van-radio-group>
      </div>
      <div class="carOwner">
        <p>是否为贷款车:</p>
        <van-radio-group v-model="radio">
          <van-radio name="1" style="width:0.9rem">是</van-radio>
          <van-radio name="2">否</van-radio>
          <!-- <van-radio name="2">机关</van-radio> -->
        </van-radio-group>
      </div>
    </div>

    <div class="btn">
      <van-button size="large" round @click="$router.push({name: 'Card'})" >下一步</van-button>
    </div>
  </div>
</template>

<script>
import { Toast } from 'vant'
export default {
  name: 'Driving',
  data () {
    return {
      username: '',
      password: '',
      checked: true,
      radio: '1'
    }
  },
  methods: {
    fileImage (e, i) {
      // var that = this
      var file = e.target.files[0]
      if (file.name.split('.')[1] !== 'png' && file.name.split('.')[1] !== 'gif' && file.name.split('.')[1] !== 'jpg' && file.name.split('.')[1] !== 'jpeg' && file.name.split('.')[1] !== 'bmp' && file.name.split('.')[1] !== 'pdf') {
        Toast('请上传图片')
      } else {
        var imgSize = file.size / 1024
        if (imgSize > 5 * 1024) {
          Toast('请上传大小不要超过5M的图片')
        } else {
          var reader = new FileReader()
          reader.readAsDataURL(file) // 读出 base64
          reader.onloadend = function () {
            var dataURL = reader.result
            e.target.previousElementSibling.src = dataURL
          }
        }
      }
    }
  }
}
</script>

<style lang="less" scoped>
.van-checkbox {
  font-size: 0.16rem;
  color: #333333;
  padding-left: 0.25rem;
  margin-top: 0.2rem;
}
.driving {
  background: #f2f2f2;
  height: calc(100% - 0.2rem);
  padding-top: 0.2rem;
  font-size: 0.16rem;
  overflow: auto;
  .upload {
    background: #fff;
    p {
      font-size: 0.17rem;
      text-align: center;
      line-height: 0.7rem;
    }
    .up {
      overflow: hidden;
      width: 2.08rem;
      margin: 0 auto;
      .box {
        width: 2.08rem;
        height: 1.4rem;
        position: relative;
        img {
          width: 100%;
        }
        .imgShow {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          background-size: 100% 100%;
          border-radius: 0.06rem;
        }
        input {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          opacity: 0;
          font-size: 0.15rem;
        }
      }
    }
    .span {
      text-align: center;
      font-size: 0.12rem;
      color: #BCBBBB;
      padding: 0.09rem 0 0.4rem;
    }
  }
  .btn {
    text-align: center;
    width: 100%;
    bottom: 0.1rem;
    margin: 0.14rem 0;
    button {
      border-radius: 0.5rem
    }
  }
  .van-field {
    border-bottom: 1px solid #F4F4F4;
  }
  .owner {
    margin-top: 0.1rem;
    background: white;
    padding-top: 0.14rem;
    padding-left: 0.12rem;
    padding-right: 0.12rem;
    font-size: 0.17rem;
    p {
      font-weight: bold;
      font-size: 0.18rem;
      margin-bottom: 0.18rem;
    }
    .van-radio-group {
      display: inline-block;
      vertical-align: sub;
      .van-radio {
        display: inline-block;
        margin-left: 0.1rem;
      }
    }
    .carOwner {
      height: 0.47rem;
      border-bottom: 1px solid #f4f4f4;
      padding: 0.1rem 0;
      box-sizing: border-box;
      span {
        color: #333333;
        font-size: 0.17rem;
        display: inline-block;
        margin-left: 0.1rem;
      }
      p {
        display: inline-block;
        width: 1.1rem;
        font-weight: 400;
        margin: 0;
        color: #333333;
        font-size: 0.17rem;
        margin-left: 0.1rem;
      }
    }
  }
  .cardUp {
    margin-top: 0.03rem;
    background: white;
    padding: 0.29rem 0.17rem;
    font-size: 0.17rem;
    display: flex;
    justify-content: space-between;
    img {
      width: 1.65rem;
      height: 1.43rem;
    }
    input {
      width: 1.65rem;
      height: 1.43rem;
      background: pink;
      position: absolute;
      top: 0;
      opacity: 0;
    }
    div {
      position: relative;
    }
  }
}
</style>
