<template>
  <view style="margin: 10px;">
    <view style="border: 1px solid #f5f5f5;border-radius: 10px;">
      <uni-list-item :title="'头像'" clickable>
        <template slot="footer">
          <image :src="testImage" class="avator"></image>
        </template>
      </uni-list-item>
      <uni-list-item :title="'姓名'" clickable :right-text="'关羽'"> </uni-list-item>
      <uni-list-item :title="'手机号'" clickable :right-text="'16622910980'"> </uni-list-item>
      <uni-list-item :title="'地址'" clickable :right-text="'XXX楼XXX层XX号'"> </uni-list-item>
      <uni-list-item :title="'切换角色'" clickable show-arrow>
        <tempalte slot="footer">
          <picker :range="timePicker" @change="timePickerChange">
            {{  timePicker[timeIndex1] }}
          </picker>
        </tempalte>
      </uni-list-item>
    </view>
    <view >
      <button class="marginTop button" type="default" style="color: red" @click="layout">退出登录</button>
      <button class="marginTop button" type="default" >注销账户</button>
    </view>
  </view>
</template>

<script>
import testImage from 'static/logo.png'
import UniListItem from "../../../uni_modules/uni-list/components/uni-list-item/uni-list-item";
export default {
  name: "settingIndex",
  components: {UniListItem},
  data(){
    return {
      testImage: testImage,
      timeIndex1: 0,
      timePicker: ['普通用户', '配送员']
    }
  },
  methods:{
    timePickerChange(e){
      this.timeIndex1 = e.detail.value[0];
    },
    layout(){
      // uni.login({
      //   provider: 'weixin',
      //   success: function (loginRes) {
      //     console.log(loginRes.authResult);
      //   }
      // });
    }
  }
}
</script>

<style scoped lang="scss">
.avator{
  width: 30px;
  height: 30px;
}
/deep/.uni-list-item{
  font-size: 16px;
  line-height: 30px;
}
/deep/.uni-list-item__content-title{
  font-size: 16px;
}
/deep/.uni-list-item__extra-text{
  font-size: 14px;
  color: #606266;
}
.button{
  background-color: white;
  font-size: 14px;
  line-height: 60px
}
/deep/uni-button:after{
  border: none;
}
</style>
