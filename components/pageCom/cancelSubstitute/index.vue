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
          :title="'退款原因'"
          :right-text="'请选择'"
          clickable
          showArrow
          @click="selectReason"

      >
        <template slot="footer">
          <picker :range="timePicker" @change="timePickerChange" mode="multiSelector">
            {{  timePicker[0][timeIndex1] }}
          </picker>
        </template>
      </uni-list-item>

      <uni-list-item
          :title="'退款金额'"
      >
        <template slot="footer">
          <view style="color: red">¥ 1</view>
        </template>
      </uni-list-item>
    </view>
    <view class="border marginTop">
      <view>补充原因</view>
      <textarea cols="30" maxlength="500" rows="6" :placeholder="reasonText"
                style="width:100%;font-size: 12px;margin-top: 8px;background-color: #c0c0c02e;border-radius: 10px">
	</textarea>
    </view>
    <view class="footer">
      <view style="margin-bottom: 30px">
        <button type="primary" v-show="!detailsInfo.isTrue" >提交</button>
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
        ['不想代取了', '赶时间自己拿', '信息填错'],
      ],
      payTypePicker:[
        ['微信'],
      ],
      range:[
        {value:0, text: '同意并接受'}
      ],
      reasonText: '补充原因，有助于我们更好的提升服务处理后续问题',
      timeIndex1: 0,
      payTypeIndex1: 0,
      timeIndex2: 0
    }
  },
  methods:{
    // 选择退款原因
    selectReason(){

    },
    timePickerChange(e){
      this.timeIndex1 = e.detail.value[0];
    },
    payTypePickerChange(e){
      this.payTypeIndex1 = e.detail.value[0];
    }
  }
}
</script>

<style scoped lang="scss">
/deep/.uni-list-item__container{
  border-bottom: 1px solid #e1e2e3;
}
/deep/.uni-list-item{
  font-size: 13px;
}
/deep/.uni-checkbox .uni-checkbox-input{
  width: 12px;
  height: 12px;
}
///deep/.uni-textarea-textarea{
//  background-color: #c0c0c02e;
//  border-radius: 10px;
//  margin: 8px;
//}
///deep/.uni-textarea-placeholder{
//  font-size: 12px;
//  margin: 10px 0 0 5px;
//}
</style>
