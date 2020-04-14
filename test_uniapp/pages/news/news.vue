<template>
	<view>
		<view v-show="false">v-show</view>
		<view v-if="false">v-if</view>
		<view>xxx</view>
		
		<button type="primary" size="mini" @click="uploadPic">上传图片</button>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad() {
			uni.setNavigationBarColor({
			    frontColor: '#ffffff',
			    backgroundColor: '#ff0000',
			    animation: {
			        // duration: 400,
			        timingFunc: 'easeIn'
			    }
			})
		},
		onReady() {
			
		},
		onShow() {
			
		},
		onHide() {
			
		},
		onPullDownRefresh() {
			console.log("下拉加载....")
		},
		methods: {
			uploadPic() {
				uni.chooseImage({
				    count: 6, //默认9
				    sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
				    sourceType: ['album'], //从相册选择
				    success: function (res) {
				        console.log(JSON.stringify(res.tempFilePaths));
				    }
				});
			}
		}
	}
</script>

<style lang="scss">

</style>
