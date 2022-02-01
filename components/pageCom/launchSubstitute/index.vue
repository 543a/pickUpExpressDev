<template>
  <view style="margin: 0 10px">
    <view class="detailsBorder marginTop">
      <view>
        <image :src="detailsInfo.src" style="width: 40px;height: 40px;border-radius: 50%"></image>
      </view>
      <view class="marginLeft centerFlex">
        <view>
          <view>{{detailsInfo.name}} {{detailsInfo.tel}}</view>
          <view>{{detailsInfo.address}}</view>
        </view>
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
    <view class="border marginTop">
<!--      <cell></cell>-->
      <uni-list-item
        :title="'期望上门时间'"
        :right-text="'今天 12：00-13：00'"
        clickable
        showArrow
        @click="selectTime"

      >
         <template slot="footer">
           <picker :range="timePicker" @change="timePickerChange" mode="multiSelector">
             {{  timePicker[0][timeIndex1] }} {{ timePicker[1][timeIndex2]  }}
           </picker>
         </template>
      </uni-list-item>

      <uni-list-item
        :title="'付款方式'"
        clickable
        showArrow
      >
        <template slot="footer">
          <picker :range="payTypePicker" @change="payTypePickerChange">
            {{  payTypePicker[payTypeIndex1] }}
          </picker>
        </template>
      </uni-list-item>
    </view>
    <view class="marginTop" style="font-size: 12px">
      <checkbox v-model="checkAgreement" style="transform: scale(0.8)">
        <view style="display: flex;font-size: 16px">
          <view>同意并接受</view>
          <view style="color: #214c0c">《协议》</view>
        </view>
      </checkbox>
<!--      <uni-data-checklist-->
<!--          selectedColor="#406936"-->
<!--          :localdata="range"-->
<!--      >-->

<!--      </uni-data-checklist>-->
<!--      <uni-data-checkbox　selectedColor＝"red" selectedTextColor="red" multiple v-model="value" :localdata="range" @change="change">-->
<!--      </uni-data-checkbox>-->
    </view>
    <view class="footer">
      <view style="margin: 0 15px">
        <uni-row >
          <uni-col :span="16" >
            <view style="display: flex;margin: 12px 5px" >
              <view>费用：</view>
              <view style="color: #153406">¥{{' 1'}}</view>
            </view>
          </uni-col>
          <uni-col :span="8">
            <button type="primary" >提交</button>
          </uni-col>
        </uni-row>
      </view>
    </view>
  </view>
</template>

<script>
import testImage from 'static/logo.png'
import UniListItem from "../../../uni_modules/uni-list/components/uni-list-item/uni-list-item";
import UniDatetimePicker
  from "../../../uni_modules/uni-datetime-picker/components/uni-datetime-picker/uni-datetime-picker";
import UniDataChecklist from "../../../uni_modules/uni-data-checkbox/components/uni-data-checkbox/uni-data-checkbox";
export default {
  name: "launchIndex",
  components: {UniDataChecklist, UniDatetimePicker, UniListItem},
  data(){
    return {
      checkAgreement: '',
      detailsInfo: {
        src: testImage,
        name: '关羽',
        tel: '166***0980',
        title: 'YT33421989-2222',
        address: 'XX学校X楼X层-503'
      },
      timePicker:[
        ['今天', '明天'],
        ['13：00-14：00', '14：00-15：00', '15：00-16：00']
      ],
      payTypePicker:[
        ['微信'],
      ],
      range:[
        {value:0, text: '同意并接受'}
      ],
      timeIndex1: 0,
      payTypeIndex1: 0,
      timeIndex2: 0
    }
  },
  methods:{
    // 选择上门时间
    selectTime(){

    },
    timePickerChange(e){
      this.timeIndex1 = e.detail.value[0];
      this.timeIndex2 = e.detail.value[1];
    },
    payTypePickerChange(e){
      this.payTypeIndex1 = e.detail.value[0];
    }
  }
}
</script>

<style scoped lang="scss">
/deep/.uni-list-item__container{
  //border-bottom: 1px solid #e1e2e3;
}
/deep/.uni-list-item{
  font-size: 13px;
}
/deep/.uni-checkbox .uni-checkbox-input{
  width: 12px;
  height: 12px;
}
</style>
