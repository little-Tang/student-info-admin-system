<template>
  <div class="my-header">
    <div class="logo">
      <router-link to="/">
        <img src="@/assets/index/logo.png" alt="">
      </router-link>
    </div>
    <el-dropdown>
      <i class="el-icon-setting" style="margin-right: 15px"></i>
      <el-dropdown-menu slot="dropdown">
        <el-dropdown-item>关于</el-dropdown-item>
        <!-- <el-dropdown-item>使用说明</el-dropdown-item> -->
        <!-- <el-dropdown-item>删除</el-dropdown-item> -->
      </el-dropdown-menu>
    </el-dropdown>
    <span>{{myname}}</span>
  </div>
</template>

<script>
import { getName } from '@/api/getName'
export default {
  name: 'MyHeader',
  data () {
    return {
      myname: 'LITTLETANG'
    }
  },
  created () {
    this.getUserName()
  },
  methods: {
    getUserName () {
      this.myname = 'Loading...'
      getName('/api/name.php').then(res => {
        console.log('then--' + res)
        this.myname = res.data.userName
      })
    }
  }
}
</script>

<style>
  .logo {
    position: absolute;
    top: 0;
    left: 20px;
  }
  .logo img {
    height: 50px;
  }
</style>
