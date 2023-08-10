<template>
  <div class="register">
    <div class="register-content">
      <div class="title">
        <span>注册</span>
      </div>
      <div class="forms">
        <el-form ref="regFormRef" :model="ruleForm" status-icon :rules="rules" label-width="120px" class="demo-ruleForm"
          label-position="top">
          <el-form-item label="用户名" prop="userName">
            <el-input v-model="ruleForm.userName" type="text" autocomplete="off" />
          </el-form-item>
          <el-form-item label="手机号" prop="userPhone">
            <el-input v-model="ruleForm.userPhone" type="userPhone" autocomplete="off" />
          </el-form-item>
          <el-form-item label="密码" prop="pass">
            <el-input v-model="ruleForm.pass" type="password" autocomplete="off" />
          </el-form-item>
          <el-form-item label="再次确认密码" prop="checkPass">
            <el-input v-model="ruleForm.checkPass" type="password" autocomplete="off" />
          </el-form-item>
          <el-form-item >
            <el-button type="primary" @click="submitForm(regFormRef)" class="button">提交</el-button>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'

const regFormRef = ref<FormInstance>()

const validateName = (rule: any, value: any, callback: any) => {
  if (value === '') {
    callback(new Error('请输入用户名'))
  } else {
    callback()
  }
}

const validatePhone = (rule: any, value: any, callback: any) => {
  var phoneRule = new RegExp(/^1[3456789]\d{9}$/)
  if (value === '') {
    callback(new Error('请输入手机号'))
  } else {
    if (ruleForm.userPhone !== '') {
      if (!phoneRule.test(value)) {
        callback(new Error('请输入正确的手机号'))
      } else {
        callback()
      }
    }
  }
}

const validatePass = (rule: any, value: any, callback: any) => {
  if (value === '') {
    callback(new Error('请输入密码'))
  } else {
    if (ruleForm.checkPass !== '') {
      if (!regFormRef.value) return
      regFormRef.value.validateField('checkPass', () => null)
    }
    callback()
  }
}
const validatePass2 = (rule: any, value: any, callback: any) => {
  if (value === '') {
    callback(new Error('请再次输入密码'))
  } else if (value !== ruleForm.pass) {
    callback(new Error("两次输入的密码不匹配"))
  } else {
    callback()
  }
}

const ruleForm = reactive({
  userName: '',
  userPhone: '',
  pass: '',
  checkPass: '',
})

const rules = reactive<FormRules<typeof ruleForm>>({
  userName: [{ validator: validateName, trigger: 'blur' }],
  pass: [{ validator: validatePass, trigger: 'blur' }],
  checkPass: [{ validator: validatePass2, trigger: 'blur' }],
  userPhone: [{ validator: validatePhone, trigger: 'blur' }],
})

const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.validate((valid) => {
    if (valid) {
      console.log('submit!')
    } else {
      console.log('error submit!')
      return false
    }
  })
}
</script>

<style scoped lang="less">
.register {
  width: 40vw;
  border: 1px solid silver;
  display: flex;
  justify-content: center;
  border-radius: 10px;

  .register-content {
    width: 30vw;
    margin:30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    .title{
      font-size: 25px;
      margin: 0 auto;
      margin-bottom: 20px;
    }
    .button{
      width: 100%;
      margin: 0 auto;
      margin-top: 30px;
    }
  }
}
</style>
