<template>
  <div class="pay">
    <div class="upload">
      <p>请填写银行卡信息和正面照片</p>
      <div class="up">
        <div class="font box">
          <img src="../assets/img/bankcard.png" alt="">
          <!-- <div class="imgShow"></div> -->
          <input type="file" accept="image/*"  @change="fileImage($event, 1)" capture="camera">
        </div>
      </div>
      <div class="span">若信息不准确，请重新上传或修改</div>
      <div class="payinput">
        <div class="input">
          <div class="tit">
            开户行:
          </div>
          <input type="text" v-model="username" placeholder="请输入开户行">
        </div>
        <div class="input">
          <div class="tit">
            银行卡号:
          </div>
          <input type="text" v-model="password" placeholder="请输入银行卡号">
        </div>
      </div>
    </div>
    <div class="payinput" style="margin-top:0.1rem">
      <div class="input">
        <div class="tit">
          手机号:
        </div>
        <input type="text" v-model="tel" placeholder="请输入手机号">
      </div>
      <div class="input" style="height: 0.6rem">
        <div class="tit">
          验证码:
        </div>
        <input type="number" v-model="password" style="width:1rem;">
        <button @click="getCode" class="fsfs">获取验证码<span v-if="codeshow">{{ count }}s</span></button>
      </div>
    </div>
    <van-checkbox v-model="checked" checked-color="#4b0">我已阅读并同意《xxxx车险协议》</van-checkbox>
    <div class="btn">
      <van-button size="large" round @click="sure" :class="{disabled: checked == false}">确定</van-button>
    </div>
    <!-- 弹窗 -->
    <van-dialog
      v-model="show"
      :showConfirmButton="false"
      :before-close="beforeClose"
    >
      <img src="../assets/img/alert.png" alt="" @click="show = false">
    </van-dialog>
  </div>
</template>

<script>
import { Toast } from 'vant'
export default {
  name: 'Pay',
  data () {
    return {
      username: '',
      password: '',
      checked: false,
      sms: '',
      tel: '',
      show: false,
      count: 60,
      codeshow: false
    }
  },
  methods: {
    getCode (e) {
      if (!(/^1[34578]\d{9}$/.test(this.tel))) {
        Toast('请输入正确的手机号')
      } else {
        if (this.codeshow === false) {
          this.codeshow = true
          e.target.className = 'disabled'
          this.clock = window.setInterval(() => {
            this.count--
            if (this.count < 1) {
              this.codeshow = false
              e.target.className = ''
              clearInterval(this.clock)
              this.count = 60
            }
          }, 1000)
        }
      }
    },
    sure () {
      this.show = true
    },
    beforeClose (action, done) {
      if (action === 'confirm') {
        setTimeout(done, 1000)
      } else {
        done()
      }
    },
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
            var avatar = dataURL
            e.target.previousElementSibling.src = avatar
          }
        }
      }
    }
  }
}
</script>

<style lang="less" scoped>
input {
  font-size: 0.16rem;
}
.van-dialog {
  width: 3rem;
  background: rgba(0,0,0,0);
  img {
    width: 3rem;
    display: block;
  }
}
.van-checkbox {
  font-size: 0.16rem;
  color: #666666;
  padding-left: 0.25rem;
  margin-top: 0.2rem;
  padding-bottom: 0.6rem;
}
.van-button {
  &.code {
    width:0.98rem;
    height:0.3rem;
    border:0.01rem solid rgba(153,153,153,1);
    border-radius:0.15rem;
    color: rgba(153,153,153,1);
    background-color: #fff;
  }
}
.pay {
  background: #f2f2f2;
  // height: calc(100% - 0.2rem);
  position: relative;
  height: 100%;
  box-sizing: border-box;
  padding-top: 0.2rem;
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
      width: 1.68rem;
      margin: 0 auto;
      .box {
        width: 1.66rem;
        height: 1.44rem;
        // border: 0.01rem solid #ccc;
        float: left;
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
        }
        input {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          opacity: 0;
        }
      }
    }
    .span {
      text-align: center;
      font-size: 0.12rem;
      color: #BCBBBB;
      padding: 0.09rem 0 0.2rem 0;
    }
  }
  .btn {
    text-align: center;
    width: 100%;
    height: 0.49rem;
    background: none;
    position: relative;
    bottom: 0.1rem;
    button {
      border-radius: 0.5rem;
    // left: 0.4rem;
    }
  }
  .payinput {
    padding: 0 0.25rem;
    background: white;
    .input {
      display: flex;
      justify-content: space-between;
      div {
        color: #666666;
      }
      input {
        text-align: right;
      }
      button {
        margin-left: 0.1rem;
        width: 1.1rem;
        height: 0.3rem;
        border: 1px solid #999999;
        border-radius: 0.5rem;
        background: white;
        color: #999999;
        font-size: 0.15rem;
      }
    }
  }
}
.disabled {
    pointer-events: none;
    cursor: default;
    opacity: 0.6;
}
</style>
