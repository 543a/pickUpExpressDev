<template>
  <view>
    <view class="detailsTitle">
      <view>运单号: {{detailsInfo.title}}</view>
      <view>{{'代签收'}}</view>
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
    <view style="margin:  20px">
      <uni-steps :options="stepOptions" direction="column" :active="3" active-color="#387519">
      </uni-steps>
    </view>
    <view style="position: fixed;bottom:0;width: 100%">
      <button type="primary" v-if="showApply">发起代取</button>
      <button type="primary" v-else>取消代取</button>
    </view>
  </view>
</template>

<script>
import testImage from 'static/logo.png'
export default {
  name: "index",
  data(){
    return {
      showApply:true,
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
  margin: 10px;
  padding: 0 10px;
  line-height: 2;
  border-radius: 15px;
  background-color: #a8d490;
}
.detailsBorder{
  margin:0 20px;
  display: flex;
  border: 1px solid #b0adad;
  padding: 20px;
  border-radius: 10px;
}
</style>
