<template>
  <view>
    <view style="position: sticky;top:0;z-index: 10000;background-color: white">
      <view class="topSearch">
        <uni-easyinput prefixIcon="search" v-model="value" placeholder="请输入内容" style="width: 100%"></uni-easyinput>
        <uni-icons type="scan" size="30"></uni-icons>
      </view>
      <view>
        <uni-segmented-control :current="current" :values="itemsOption" @clickItem="onClickItem" styleType="text" activeColor="#4cd964"></uni-segmented-control>
      </view>
    </view>
    <view>
      <!--      <uni-load-more :status="more">-->
      <uni-list >
        <uni-list-item
            class="listItem"
            v-for="item in expressList"
            :key="item.id"
            :title="item.title"
            :thumb="item.src"
            :note="item.note"
        >
          <template slot="header">
            <image :src="item.src" style="border-radius: 50%;width: 50px;height: 50px"></image>
          </template>
        </uni-list-item>
      </uni-list>
      <!--      </uni-load-more>-->
    </view>
  </view>
</template>

<script>
import testImage from 'static/logo.png'
import UniListChat from "../../uni_modules/uni-list/components/uni-list-chat/uni-list-chat";
import UniIcons from "../../uni_modules/uni-icons/components/uni-icons/uni-icons";
export default {
  name: "substitute",
  components: {UniIcons, UniListChat},
  data(){
    return {
      value: '',
      current: 0,
      more: 'more',
      itemsOption: ['代取订单', '历史订单' ],
      expressList: [
        { id: 1, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 2, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 3, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 4, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 5, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 6, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 7, src:testImage, title: '运单号：YT33444333', note: `取件码 W-12-1209\n代取中` },
        { id: 8, src:testImage, title: '运单号：YT32122222', note: '取件码 W-12-1209\n待取中' },
      ]
    }
  },
  methods:{
    // 选项卡切换
    onClickItem(){
      console.log(3)
    },
    search(){
      console.log('唤起摄像头')
    },
    scanning(){
      console.log('唤起摄像头')
    }
  }
}
</script>

<style scoped lang="scss">
.topSearch{
  display: flex;
  align-items: center;
  padding: 20px 10px;
}
/deep/.uni-list-item__container{
  align-items: center;
}
/deep/.uni-list-item__content--center{
  margin-left: 20px;
}
.listItem{
  /deep/uni-button[size=mini]{
    line-height: 2.4;
    font-size: 3px;
  }
}
</style>
