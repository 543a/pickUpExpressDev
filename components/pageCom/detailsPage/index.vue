<template>
  <view style="margin: 10px">
    <view class="detailsTitle">
      <view>运单号: {{detailsInfo.title}}</view>
      <view>{{detailsInfo.isTrue==true?'待签收': detailsInfo.isGet? '已签收': '已接单'}}</view>
    </view>
    <view class="detailsBorder">
      <view>
        <image :src="detailsInfo.src" style="width: 70px;height: 70px;border-radius: 50%"></image>
      </view>
      <view class="marginLeft">
        <view>{{'圆通快递'}}</view>
        <view>运单号：{{detailsInfo.title}}</view>
        <view>取件码：{{detailsInfo.note}}</view>
      </view>

<!--      <uni-list-item-->
<!--          class="listItem"-->
<!--          :title="detailsInfo.title"-->
<!--          :thumb="detailsInfo.src"-->
<!--          :note="detailsInfo.note"-->
<!--      >-->
<!--        <template slot="header">-->
<!--          <image :src="detailsInfo.src" style="border-radius: 50%;width: 50px;height: 50px"></image>-->
<!--        </template>-->
<!--      </uni-list-item>-->
    </view>
    <!--      进度信息-->
    <view class="detailsBorder" >
      <uni-steps :options="stepOptions" direction="column" :active="3" active-color="#387519">
      </uni-steps>
    </view>
    <view class="footer">
      <view style="margin: 10px 15px">
        <uni-row v-if="detailsInfo.isGet" >
          <uni-col :span="16" >
            <view @click="pickQrcode">
              <view style="margin-left: 10px">
                <image :src="ericon" style="width: 20px; height: 20px;"></image>
              </view>
              <view>签收码</view>
            </view>
          </uni-col>
          <uni-col :span="8">
            <button type="primary" >确认送达</button>
          </uni-col>
        </uni-row>
      </view>
      <view style="margin-bottom: 30px" v-if="!detailsInfo.isGet">
        <button type="primary" v-show="detailsInfo.isTrue" @click="launchSub">发起代取</button>
        <button type="primary" v-show="!detailsInfo.isTrue" @click="cancelSub">取消代取</button>
      </view>
    </view>
    <uni-popup  ref="popup" type="center" background-color="white" animation>
      <view style="margin: 20px">
        <image :src="ericon"></image>
      </view>
    </uni-popup>
  </view>
</template>

<script>
import testImage from 'static/logo.png'
import ericon from 'static/image/ericon.png'
export default {
  name: "index",
  data(){
    return {
      showApply:true,
      ericon: ericon,
      detailsInfo: {},
      stepOptions: [
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '您的快件已到达XXX站点'},
        { title: '2020-12-14 08:34:34', desc: '已发货'},
      ]
    }
  },
  methods:{
    // 发起代取
    launchSub(){
      console.log(333)
      uni.navigateTo({
        url: '/components/pageCom/launchSubstitute/index',
      })
    },
    // 取消代取
    cancelSub(){
      uni.navigateTo({
        url: '/components/pageCom/cancelSubstitute/index'
      })
    },
    // 唤起二维码
    pickQrcode(){
      this.$refs.popup.open('center')
    }
  },
  onLoad(options){
    this.detailsInfo = JSON.parse(options.item)
    this.detailsInfo.src = testImage
    console.log(JSON.parse(options.item), 'here')
  }
}
</script>

<style scoped lang="scss">
.detailsTitle{
  display: flex;
  justify-content: space-between;
  //margin: 10px;
  padding: 0 10px;
  line-height: 2;
  border-radius: 15px;
  background-color: #a8d490;
}

</style>
