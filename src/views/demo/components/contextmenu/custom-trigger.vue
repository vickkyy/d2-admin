<template>
  <d2-container :filename="filename" type="card">
    <template slot="header">自定义事件</template>
    <v-contextmenu ref="contextmenu">
      <v-contextmenu-item @click="handleClick">菜单1</v-contextmenu-item>
      <v-contextmenu-item divider></v-contextmenu-item>
      <v-contextmenu-item @click="handleClick">菜单2</v-contextmenu-item>
      <v-contextmenu-item @click="handleClick">菜单3</v-contextmenu-item>
    </v-contextmenu>
    <v-contextmenu ref="dbContextmenu" event-type="dblclick">
      <v-contextmenu-item @click="handleClick">菜单1</v-contextmenu-item>
      <v-contextmenu-item divider></v-contextmenu-item>
      <v-contextmenu-item @click="handleClick">菜单2</v-contextmenu-item>
      <v-contextmenu-item @click="handleClick">菜单3</v-contextmenu-item>
    </v-contextmenu>
    <el-row :gutter="20">
      <el-col :span="12">
        <div class="contextmenu-pad" v-contextmenu:contextmenu>
          右键点击此区域
        </div>
      </el-col>
      <el-col :span="12">
        <div class="contextmenu-pad" v-contextmenu:dbContextmenu>
          左键双击此区域
        </div>
      </el-col>
    </el-row>
  </d2-container>
</template>

<script>
export default {
  data () {
    return {
      filename: __filename
    }
  },
  methods: {
    handleClick (instance, event) {
      this.$message({
        message: `你点击了${instance.$slots.default[0].text}`,
        type: 'info'
      })
    }
  }
}
</script>

<style lang="scss" scoped>
@import './style/pub.scss';
</style>
