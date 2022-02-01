<template>
  <view>
    <view style="position: sticky;top:0;z-index: 10000;background-color: white">
      <view class="topSearch">
        <uni-easyinput prefixIcon="search" v-model="value" placeholder="请输入内容" style="width: 100%"></uni-easyinput>
        <uni-icons type="scan" size="30" @click="scanning"></uni-icons>
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
            :title="`运单号：${item.title}`"
            :thumb="item.src"
            :note="`取件码:${item.note}\n${item.status}`"
            :clickable="true"
            @click="toDetailsInfo(item)"
        >
          <template slot="header">
            <image :src="item.src" style="border-radius: 50%;width: 50px;height: 50px"></image>
          </template>
          <template slot="footer" >
            <button v-if="item.isTrue" size="mini" @click.stop="launchSub" :hover-stop-propagation="true">发起代取</button>
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
  name: "list",
  components: {UniIcons, UniListChat},
  data(){
    return {
      value: '',
      current: 0,
      more: 'more',
      itemsOption: ['未签收', '已签收' ],
      expressList: [
        { id: 1, src:testImage, title: 'YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: true},
        { id: 2, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: true},
        { id: 3, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        { id: 4, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        { id: 5, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        { id: 6, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        { id: 7, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        { id: 8, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        { id: 9, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
      ]
    }
  },
  methods:{
    // 选项卡切换
    onClickItem(obj){
      if (obj.currentIndex==0){
        this.expressList = [
          { id: 1, src:testImage, title: 'YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: true},
          { id: 2, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: true},
          { id: 3, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
          { id: 4, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
          { id: 5, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
          { id: 6, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
          { id: 7, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
          { id: 8, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
          { id: 9, src:testImage, title: ' YT33444333', note: `W-12-1209`, status: '代取中' , isTrue: false},
        ]
      }else{
        this.expressList = [
          { id: 1, src:testImage, title: 'YT33444333', note: `W-12-1209`, status: '代取中', isGet: true },
          { id: 2, src:testImage, title: 'YT33444333', note: `W-12-1209`, status: '代取中', isGet: true},
          { id: 3, src:testImage, title: 'YT33444333', note: `W-12-1209`, status: '代取中', isGet: true}
        ]
      }
    },
    search(){
      console.log('唤起摄像头')
    },
    scanning(){
      console.log('唤起摄像头')
      uni.scanCode({
        success(result){
          console.log(result)
        }
      })
    },
    // 详情页跳转
    toDetailsInfo(item){
      uni.navigateTo({
        url: '../../components/pageCom/detailsPage/index?item=' + JSON.stringify(item)
      })
      console.log(item,'item')
    },
    // 发起代取
    launchSub(){
      uni.navigateTo({
        url: '../../components/pageCom/launchSubstitute/index'
      })
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

.listItem{
  /deep/.uni-button[size=mini]{
    line-height: 2.4;
    font-size: 3px;
  }
}
/deep/.uni-list{
  background-color: #f5f5f5;
}
</style>
