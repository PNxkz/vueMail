<template>
  <div class="footer">
    <div class="footer-loge">
      <img src="../../public/imgs/logo-footer.png" alt="">
      <p>小米商城</p>
    </div>
    <div class="footer-link">
      <a href="">pn的主页</a><span>|</span>
      <a href="">vue全家桶</a><span>|</span>
      <a href="">react全家桶教学</a><span>|</span>
      <a href="">微信小程序支付</a>
    </div>
    <div class="copyright">Copyright 2019 <span class="domain">mi.futurefe.com</span> All right server</div>
  </div>
</template>
<script>
  export default{
      name:'nav-footer',
  }
</script> 
<style lang="scss" scoped>
.footer{
  height: 234px;
  border-top: 4px solid #FF6600;
  background-color: #333333;
  color: #999999;
  font-size: 16px;
  text-align: center;
  .footer-loge{
    margin-top: 46px;
    margin-bottom: 31px;
    img{
      width: 53px;
      height:36px;
      margin-bottom: 13px;
    }
  }
  .footer-link{
    margin-bottom: 13px;
    a{
      color:#999999;
      display: inline-block;
    }
    span{
      margin: 0 10px;
    }
  }
  .copyright{
    .domain{
      color:#FF6600
    }
  }
}
</style>