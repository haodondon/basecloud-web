<template >

 <div id="peripheral">

    <div id="msg">
        <el-carousel :interval="4000" arrow="never">
            <el-carousel-item>
                <img src="../assets/pic/1.jpg" width="100%" height="100%" alt="" srcset="">
            </el-carousel-item>
            <el-carousel-item>
                <img src="../assets/pic/2.jpg" width="100%" height="100%" alt="" srcset="">
            </el-carousel-item>
            <el-carousel-item>
                <img src="../assets/pic/3.jpg" width="100%" height="100%" alt="" srcset="">
            </el-carousel-item>
        </el-carousel>
    </div>
    <div id="loginInfo">

        <div id="loginTitle">
            BaseCloud云平台
        </div>

        <div style="margin-top: 40px;">

            <el-tabs v-model="activeName" @tab-click="handleClick">

                <el-tab-pane  label="账户密码登录" name="first">
                    <el-form :model="accountLogin" :rules="accountLoginRules" ref="accountLogin" label-width="100px" >

                        <el-form-item label="" prop="account">
                            <el-input
                                placeholder="账号"
                                clearable
                                autocomplete="off"
                                v-model="accountLogin.account">
                                <i slot="prefix" class="el-input__icon el-icon-user"></i>
                            </el-input>
                        </el-form-item>
                        <el-form-item label="" prop="passWord">
                            <el-input
                                placeholder="密码"
                                clearable
                                autocomplete="off"
                                v-model="accountLogin.passWord"
                                show-password>
                                <i slot="prefix" class="el-input__icon el-icon-unlock"></i>
                            </el-input>
                        </el-form-item>
                        <el-button type="primary" @click="accountLoginSubmit('accountLogin')" style="width: 314px;margin: 78px;" round>登录</el-button>
                    </el-form>
                </el-tab-pane>
                <el-tab-pane  label="手机号登录" name="second">
                    <el-form :model="phoneLogin" :rules="phoneLoginRules" ref="phoneLogin" label-width="100px" >

                        <el-form-item label="" prop="phone">
                            <el-input
                                placeholder="手机号"
                                clearable
                                v-model="phoneLogin.phone">
                                <i slot="prefix" class="el-input__icon el-icon-user"></i>
                            </el-input>
                        </el-form-item>
                        <el-form-item label="" prop="vCode" style="width: 60%;">
                            <el-input
                                placeholder="验证码"
                                clearable
                                maxlength="6"
                                v-model="phoneLogin.vCode">
                                <i slot="prefix" class="el-input__icon el-icon-unlock"></i>
                                
                            </el-input>
                        </el-form-item>
                        <el-button type="primary" @click="phoneLoginSubmit('phoneLogin')" style="width: 314px;margin: 78px;" round>登录</el-button>

                    </el-form>
                </el-tab-pane>
            </el-tabs>

        </div>

    </div>

</div>
    
</template>

<script>
export default {

    data() {
        var accountCheck = (rule, value, callback) => {
            if (!value) {
                return callback(new Error('用户名不能为空'));
            }
            // 待完善校验
        };
        var passWordCheck = (rule, value, callback) => {
            if (!value) {
                return callback(new Error('密码不能为空'));
            }
            // 待完善校验
        };
        var phoneCheck = (rule, value, callback) => {
            if (!value) {
                return callback(new Error('手机号不能为空'));
            }
            // 待完善校验
        };
        var vCodeCheck = (rule, value, callback) => {
            if (!value) {
                return callback(new Error('验证码不能为空'));
            }
            // 待完善校验
        };
      return {
        activeName: 'first',
        accountLogin: {
          account: '',
          passWord: '',
        },
        accountLoginRules: {
          account: [
            { validator: accountCheck, trigger: 'blur' }
          ],
          passWord: [
            { validator: passWordCheck, trigger: 'blur' }
          ]
        },
        phoneLogin: {
          phone: '',
          vCode: '',
        },
        phoneLoginRules: {
          phone: [
            { validator: phoneCheck, trigger: 'blur' }
          ],
          vCode: [
            { validator: vCodeCheck, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      handleClick(tab, event) {
        console.log(tab, event);
      },
      accountLoginSubmit(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      phoneLoginSubmit(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
    }

}
</script>

<style>

html, body {
    margin: 0; 
    padding: 0;
    height: 100%;
    display: flex;
    justify-content: center; /* 水平居中 */
    align-items: center;     /* 垂直居中 */
    background-color: #f7f4f4;
}

#peripheral{

    width: 1220px;
    height: 725px;
    display: flex;

}

#msg{

    width: 750px;
    background: #409EFF;
}

#loginInfo{
    width: 470px;
    background: #ffffff;
}
.el-carousel__indicators {

    display: none;

}
.el-carousel__container {
    height: 725px;
}
.el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 725px;
    margin: auto;
    margin: 0;
  }
  
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }

#loginTitle{
    margin-top: 150px;
    font-size: xxx-large;
    font-family: inherit;
    font-style: oblique;
    text-align: center;
}

.el-tabs__nav-wrap::after {
    display: none;
}
.el-tabs__nav-scroll {
    text-align: center;
}
.el-tabs__nav {

    width: 470px;

}

.el-tabs__active-bar{
    transform: translateX(255px);
    display: none;
}

.el-tabs__item{
    font-size: 18px;
    font-style: oblique;
    font-weight: 600;
}
.el-input {
    position: relative;
    font-size: 14px;
    display: inline-block;
    width: 81%;
    margin: 10px 45px;
    margin-left: 0px;
}
.el-form-item__content{
    margin-left: 70px !important ;
}
</style>