<template>
  <view >
    <view style="background-color: #26722e26">
        <view style="padding: 15px;">
          <view class="title">
            <view>
              <image :src="userInfo.src" class="avator"></image>
            </view>
            <view class="marginLeft" style="line-height: 30px">
              <view>Hi, {{userInfo.name}}</view>
              <view>{{ userInfo.tel }}</view>
            </view>
            <view>
              <image class="settingIcon" :src="setting" @click="settingInfo"></image>
            </view>
          </view>
          <view class="address">地址信息: {{userInfo.address}}</view>
        </view>
      </view>
    <view class="border listOuter">
      <view>
        <image :src="userInfo.src" class="listImage"></image>
        <view>支付记录</view>
      </view>
      <view>
        <image :src="userInfo.src" class="listImage"></image>
        <view >收件码</view>
      </view>
      <view>
        <image :src="userInfo.src" class="listImage"></image>
        <view >联系客服</view>
      </view>
    </view>
  </view>
</template>

<script>
import testImage from 'static/logo.png'
import setting from 'static/image/setting.png'
export default {
  name: "personInfo",
  data(){
    return {
      setting: setting,
      userInfo:{
        src: testImage,
        name: '关羽',
        tel: '16622910980',
        address:'XXXX大学XXX校区XXX楼XX层XX号'
      }
    }
  },
  methods:{
    settingInfo(){
      uni.navigateTo({
        url: '/components/pageCom/settingInfo/settingIndex',
      })
    }
  }
}
</script>

<style scoped lang="scss">
.settingIcon{
  width: 25px;
  height: 25px;
  position: absolute;
  right: 20px;
  top: 40px
}
.address{
  margin: 10px 10px 30px 0;
  color: grey;
  font-size: 14px
}
.title{
  display: flex;
  align-items: center
}
.avator{
  width: 80px;
  height: 80px;
  border-radius: 50%
}
.listImage{
  border-radius: 50%;
  width: 40px;
  height: 40px;
  margin: 0 auto;
}
.listOuter{
  display: flex;
  text-align: center;
  justify-content: space-around;
  margin: -20px 10px
}
</style>
