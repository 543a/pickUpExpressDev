<script>
	export default {
		onLaunch: function() {
			console.warn('当前组件仅支持 uni_modules 目录结构 ，请升级 HBuilderX 到 3.1.0 版本以上！')
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	@import '@/uni_modules/uni-scss/index.scss';
	/* #ifndef APP-NVUE */
	@import '@/static/customicons.css';
	// 设置整个项目的背景色
	page {
		background-color: #f5f5f5;
	}

	/* #endif */
	.example-info {
		font-size: 14px;
		color: #333;
		padding: 10px;
	}
  // 列表项边框，间距颜色
  .listItem{
    border-radius: 15px;
    border: 1px solid #f1f2f3;
    margin: 8px
  }
  // 列表项区域颜色
  .bgColor{
    background-color: #dfe1e3
  }
  /deep/.uni-list-item__content--center{
    margin-left: 20px;
  }
  .marginLeft{
    margin-left: 20px;
  }
</style>
