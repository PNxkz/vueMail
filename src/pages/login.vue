<template>
  <div class="login">
    <div class="container">
      <a href="" class="banner-a"><img src="/imgs/login-logo.png" alt=""></a>
    </div>
    <div class="wrapper">
      <div class="container">
        <div class="login-form">
          <h3>
            <span class="checked">账号登陆</span>
            <span class="sep-line">|</span>
            <span>扫码登陆</span>
          </h3>
          <div class="input">
            <input type="text"  placeholder="请输入账号" v-model="username">
          </div>
          <div class="input">
            <input type="text"  placeholder="请输入密码" v-model="password">
          </div>
          <div class="btn-box">
            <a href="javascript:;" class="btn" @click="login">登陆</a>
          </div>
          <div class="tips">
            <div class="sms" @click="register">手机短信登陆/注册</div>
            <div class="reg">立刻注册<span>|</span>忘记密码？</div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="footer-link">
        <a href="">简体</a><span>|</span>
        <a href="">繁体</a><span>|</span>
        <a href="">English</a><span>|</span>
        <a href="">常见问题</a><span>|</span>
        <a href="">隐私政策</a>
      </div>
      <p class="copyright">小米公司版权所有-京ICP备xxxxx-京公网安备xxxx号-京ICP证110507号</p>
    </div>
  </div>
</template>
<script>
export default {
  name:'login',
  data(){
    return{
      username:'',
      password:'',
      userId:'',
      res:{}
    }
  },
  methods:{
    login(){
      let { username,password } = this;
      this.axios.post('/user/login',{
        username,
        password
      }).then((res)=>{
        this.$cookie.set('userId',res.id,{expires:'1M'});
        //to-do 保存用户名
        this.$router.push('/index');
      })
    },
    register(){
      this.axios.post('/user/register',{
        username:'admin123',
        password:'123',
        email:'admin123@163.com'
      }).then(()=>{
        alert('注册成功');
      })
    }
  }
}
</script>
<style lang="scss">
@import './../assets/scss/mixin.scss';
  .login{
    &>.container{
      height:113px;
      img{
        width:auto;
        height:100%;
      }
    }
    .wrapper{ 
      background: url('/imgs/login-bg.jpg') no-repeat center;
      .container{
        height:576px;
        .login-form{
          box-sizing: border-box;
          padding-left: 31px;
          padding-right: 31px;
          position: absolute;
          width: 410px;
          height: 510px;
          background-color:#ffffff;
          bottom:29px;
          right: 0;
          h3{
            line-height:23px;
            font-size:24px;
            text-align:center;
            margin: 40px auto 49px;
            .checked{
              color:#FF6600;
            }
            .sep-line{
              margin:0 32px;
            }
          }
          .input{
            width: 348px;
            height: 50px;
            text-align: center;
            border:1px solid #E5E5E5;
            margin-bottom:20px;
            input{
              width: 90%;
              height: 100%;
              border: none;
              padding-left:18px;
            }
          }
          .btn{
            width:100%;
            line-height:50px;
            margin-top:10px;
            font-size:16px;
          }
          .tips{
            margin-top:14px;
            display: flex;
            justify-content: space-between;
            cursor:pointer;
            .sms{
              color:#FF6600;
            }
            .reg{
              color:#999999;
              span{
                margin:0 7px;
              }
            }
          }
        }
      }
    }
    .footer{
      height:100px;
      padding-top:60px;
      color:#999999;
      font-size:16px;
      text-align:center;
      .footer-link{
        a{
          color:#999999;
          display:inline-block;
        }
        span{
          margin:0 10px;
        }
      }
      .copyright{
        margin-top:13px;
      }
    }
  }
</style>