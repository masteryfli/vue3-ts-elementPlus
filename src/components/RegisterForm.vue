<template>
    <el-form
        ref="registerForm"
        :model="registerUser"
        :rules="registerRules"
        label-width="100px"
        class="registerForm sign-up-form signin-signup-register">
        <el-form-item label="用户名" prop="name">
        <el-input
            v-model="registerUser.name"
            placeholder="Enter UserName..."
        ></el-input>
        </el-form-item>
        <el-form-item label="邮箱" prop="email">
        <el-input
            v-model="registerUser.email"
            placeholder="Enter Email..."
        ></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
        <el-input
            v-model="registerUser.password"
            type="password"
            placeholder="Enter Password..."
        ></el-input>
        </el-form-item>
        <el-form-item label="确认密码" prop="password2">
        <el-input
            v-model="registerUser.password2"
            type="password"
            placeholder="Enter Password..."
        ></el-input>
        </el-form-item>

        <el-form-item label="选择身份">
        <el-select v-model="registerUser.role" placeholder="请选择身份">
            <el-option label="管理员" value="admin"></el-option>
            <el-option label="用户" value="user"></el-option>
            <el-option label="游客" value="visitor"></el-option>
        </el-select>
        </el-form-item>

        <el-form-item>
        <el-button
            @click="handleRegister('registerForm')"
            type="primary"
            class="submit-btn"
            >注册</el-button
        >
        </el-form-item>
    </el-form>
</template>

<script lang="ts">
import { ref, getCurrentInstance } from "vue";

export default {  
    props: {
        registerUser: {
            type: Object,
            required: true
        },
        registerRules: {
            type: Object,
            required: true
        }
    },

    setup() {
        // @ts-ignore
        const { ctx } = getCurrentInstance();
        const handleRegister = (formName: string) => {
            ctx.$refs[formName].validate((valid: boolean) => {
                if (valid) {
                    alert("submit!");
                } else {
                    console.log("error submit!!");
                    return false;
                }
            });
        };

        return {handleRegister}
    }
}
</script>

<style scoped>

    /* 控制login & register显示 */
    form {
        padding: 0rem 5rem;
        transition: all 0.2s 0.7s;
        overflow: hidden;
    }

    /* register */
    .registerForm {
        margin-top: 20px;
        background-color: #fff;
        padding: 20px 40px 20px 20px;
        border-radius: 5px;
        box-shadow: 0px 5px 10px #cccc;
    }

    .signin-signup-register {
        transform: translate(-50%, -100%);
    }

    /* 控制login & register显示 */
    form {
        padding: 0rem 5rem;
        transition: all 0.2s 0.7s;
        overflow: hidden;
    }

    form.sign-up-form {
        opacity: 0;
        z-index: 1;
    }
</style>