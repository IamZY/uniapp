<template>
	<view>
		<view v-show="false">v-show</view>
		<view v-if="false">v-if</view>
		<view>xxx</view>
		
		<swiper indicator-dots="true" autoplay="true" interval="5000" @change="test">
			<swiper-item>
				<image src="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg"></image>
			</swiper-item>
			<swiper-item>
				<image src="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg"></image>
			</swiper-item>
			<swiper-item>
				<image src="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg"></image>
			</swiper-item>
		</swiper>
		
		
		<scroll-view scroll-x="true" style="white-space: nowrap;">
			<view id="demo1" style="display: inline-block;width:200px;height:100px;background:red">A</view>
			<view id="demo2" style="display: inline-block;width:200px;height:100px;background:yellow">B</view>
			<view id="demo3" style="display: inline-block;width:200px;height:100px;background:blue">C</view>
		</scroll-view>
		
		<view class="ld">
			<view class="left">
				<view v-for="(item,index) in list" :key="index" @click="setId(index)">
					{{item.titile}}
				</view>
			</view>
			<view class="right">
				<scroll-view :scroll-y="true" style="white-space: nowrap;height: 200px;" :scroll-into-view="clickId">
					<view v-for="(item,index) in list" :key="index">
						<view class="title" :id="'po' + index">{{item.titile}}</view>
						<view v-for="(it,idx) in item.list" :key="idx">
							{{it}}
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		
		
		<button type="primary" size="mini" @click="uploadPic">上传图片</button>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [
					{titile:"中餐",list:["鸡排饭","猪排饭","牛排饭","咖喱饭"]},
					{titile:"西餐",list:["牛排","意面","芝士","汉堡"]},
					{titile:"法餐",list:["AAA","BBB","CCC","DDD"]},
					{titile:"快餐",list:["薯条","丸子","饮料","可乐"]},
				],
				clickId: ""
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
			},
			test(e) {
				console.log(e.detail.current)
			},
			setId(index) {
				this.clickId = "po" + index;
			}
		}
	}
</script>

<style lang="scss">

	
.ld{
	display: flex;
	.left {
		width: 100px;
		border: 1px solid red;
		
	}
	.right {
		flex: 1;
	}
}

.title{
	font-size: 20px;
	font-weight: bold;
	background: pink;
}
</style>
