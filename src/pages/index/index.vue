<template>
  <view class="index">
    <view>
      <img :src="logo" alt="" style="width: 200px; height: 200px;">
    </view>
    {{ msg }}
    <view class="btn">
      <nut-button type="info" @click="handleClick('text', msg2, true)">点我</nut-button>
    </view>
    <nut-toast :msg="msg" v-model:visible="show" :type="type" :cover="cover" />
  </view>
</template>

<script>
import { reactive, toRefs } from 'vue';
import logo from "../../assets/logo.png";
export default {
  name: 'Index',
  data() {
    return {
      logo
    }
  },
  components: {

  },
  setup(){
    const state = reactive({
      msg: '欢迎使用 QJ-Cli 开发小程序',
      msg2: '你成功了～',
      type: 'text',
      show: false,
      cover: false
    });

    const handleClick = (type, msg, cover = false) => {
      state.show = true;
      state.msg2 = msg;
      state.type = type;
      state.cover = cover;
    };

    return {
      ...toRefs(state),
      handleClick
    }
  }
}
</script>

<style lang="scss">
.index {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
