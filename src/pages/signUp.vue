<template>
  <div class="register-content">
    <div class="title">
      <h1>注册</h1>
    </div>
    <div class="forms">
      <el-form ref="regFormRef" :model="regForm" status-icon :rules="rules" label-width="120px" class="demo-ruleForm" label-position="top">
        <el-form-item label="用户名" prop="userName">
          <el-input v-model="ruleForm.userName" type="password" autocomplete="off" />
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
        <el-form-item>
          <el-button type="primary" @click="submitForm(regForm)">提交</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'

const regFormRef = ref<FormInstance>()

const validatePhone = (rule: any, value: any, callback: any) => {
  var phoneRule = new RegExp(/^1[3456789]\d{9}$/)
  if (value === ''){
    callback(new Error('请输入手机号'))
  }else{
    if (ruleForm.userPhone !== ''){
      if (!phoneRule.test(value)) return
      
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
  pass: [{ validator: validatePass, trigger: 'blur' }],
  checkPass: [{ validator: validatePass2, trigger: 'blur' }],
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

<style scoped></style>
