<template>
  <div id="app">
    <el-card class="login-card">
      <!-- lottieを追加 -->
      <lottie class="login-lottie" :options="welcomeLottie" :height="300" :width="300" :animCreated="handleAnimation"/>
      <div class="login-title">ログイン</div>
      <el-form :model="loginForm">
          <el-form-item label="メールアドレス" prop="email">
              <el-input type="text" v-model="loginForm.email" autocomplete="off"></el-input>
          </el-form-item>
          <el-form-item label="パスワード" prop="password">
              <el-input type="password" v-model="loginForm.password" autocomplete="off"></el-input>
          </el-form-item>
          <el-button type="primary" :loading="checking" @click="handleLogin">ログイン</el-button>
      </el-form>
    </el-card>
  </div>
</template>

<script>
// Lottieを使用
import Lottie from "@/components/Lottie.vue"
// 動く顔のアニメーション
import * as welcome from "@/assets/welcome.json"

export default {
  name: 'app',
  // 追加
  components: {
    Lottie
  },
  data () {
    return {
      checking: false,
      loginForm: {
        email: '',
        password: '',
      }
    }
  },
  // 追加
  computed: {
    welcomeLottie () {
      return { animationData: welcome }
    }
  },
  methods: {
    // 追加
    handleAnimation (anim) {
      this.anim = anim
    },
    handleLogin() {
      this.checking = true
    }
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #E0EAF6;
  }

  .login-title {
    font-size: 32px;
    font-weight: 600;
    margin-bottom: 20px;
  }

  .login-card {
    max-width: 800px;
    margin: 200px auto 0;
    /* 動く顔の位置調整のため */
    padding: 120px 0 20px;
  }

  /* 動くやつの位置調整 */
  .login-lottie {
    position: absolute;
    top: 32px;
    right: 0;
    bottom: 0;
    left: 0;
    margin: 0 auto;
  }
</style>