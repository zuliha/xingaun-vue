<template>
    <!-- 登录表单的容器 -->
    <div class="login_container">
        <!-- 登录区域 -->
        <div class="login_box">
            <!--  头像-->
            <div class="avatar_box">
                <img src="../assets/img/tx.gif" alt="">
            </div>
            <!-- 表单 -->
            <div>
                <el-form :model="loginForm" :rules="loginRules" ref="loginForm" label-width="0px" class="login_Form">

                    <el-form-item label="" prop="username">
                        <el-input v-model="loginForm.username" prefix-icon="el-icon-user-solid"></el-input>
                    </el-form-item>

                    <el-form-item label="" prop="password">
                        <el-input v-model="loginForm.password"prefix-icon="el-icon-lock"></el-input>
                    </el-form-item>


                            <el-form-item class="login_btn">
                                <el-button type="primary" @click="submitForm('loginForm')">立即创建</el-button>
                                <el-button @click="resetForm('loginForm')">重置</el-button>
                            </el-form-item>
                </el-form>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                loginForm: {
                    username: '',
                    password: '',
                    region: '',
                    date1: '',
                    date2: '',
                    delivery: false,
                    type: [],
                    resource: '',
                    desc: ''
                },

                loginRules: {
                    name: [{
                        required: true,
                        message: '请输入用户名称',
                        trigger: 'blur'
                    }, {
                        min: 3,
                        max: 15,
                        message: '长度在 3 到15 个字符',
                        trigger: 'blur'
                    }],
                    password: [{
                        required: true,
                        message: '请输入登录密码',
                        trigger: 'blur'
                    }, {
                        min: 3,
                        max: 15,
                        message: '长度在 3 到 15 个字符',
                        trigger: 'blur'
                    }]
                }
            };
        },
        methods: {
            submitForm(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        this.$router.push("/main")
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            resetForm(formName) {
                this.$refs[formName].resetFields();
            }
        }
    }
</script>

<style lang="less" scoped>
    .Login_container {
        height: 100%;
        background-color: pink;
    }
    
    .login_box {
        width: 450px;
        height: 380px;
        background-color: blanchedalmond;
        border-radius: 3px;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }
    
    .avatar_box {
        width: 130px;
        height: 130px;
        border: 1px solid #eee;
        border-radius: 50%;
        padding: 10px;
        box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
        margin: -65px auto;
        background-color: #fff;
    }
    
    img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background-color: #eee;
    }
    
    .login_Form {
        position: absolute;
        bottom: 0px;
        width: 100%;
        padding: 0px 20px;
        box-sizing: border-box;
    }
    
    .login_btn {
        display: flex;
        justify-content: flex-end;
    }
</style>