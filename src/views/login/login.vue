<template>
  <div class="login-wrap">
    <div class="login-box">
      <el-form class="login-form" ref="formRef" :model="form" label-width="120px" label-suffix=":">
        <el-form-item label="账号">
          <el-input v-model="form.loginName" />
        </el-form-item>
        <el-form-item label="密码">
          <el-input v-model="form.password" type="password" autocomplete="off" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm(formRef)">登录</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'
import type { FormInstance } from 'element-plus'

type myForm = {
  loginName: String
  password: String
}

const formRef = ref<FormInstance>()

const form = reactive<myForm>({
  loginName: '',
  password: ''
})

const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return
  formEl.validate(valid => {
    if (valid) {
      console.log(form)
    } else {
      console.log('error submit!')
      return false
    }
  })
}
</script>

<style lang="less">
@width: 500px;
@height: 500px;
.login-wrap {
  width: 100%;
  height: 100%;
}
.login-box {
  width: @width;
  height: @height;
  margin: 0 auto;
  display: flex;
  align-content: center;
}
</style>
