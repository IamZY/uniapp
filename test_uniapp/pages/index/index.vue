<template>
	<view class="content">
		<!-- <image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view> -->
		<!-- <test :msg1="msg" @testShowName="testEvent"></test> -->
		<text>我是首页</text>
		<view>{{"ntuzy"}}</view>
		<view>{{msg + "ntuzy"}}</view>
		<view>{{"ntuzy".indexOf("n") != -1 ? 'y':'c'}}</view>
		<view>{{"我爱北京天安门".slice(0,1)}}</view>
		
		<image src="../../static/logo.png"></image>
		
		<view :class="'box1' + 1"></view>
		
		<view :style="{width:'100px',height:'100px',background:'red'}"></view>
		
		<view :class="{box111:true}"></view>
		
		<view>
			<view 
				v-for="(item,index) in names" 
				:key="index" 
				:class="{box111:index === currentIndex}"
				@click="setIndexItem(index)"
				>
				{{item}}
			</view>
		</view>
		
		<button type="primary" @click="toPath">toNews</button>
		
	</view>
</template>

<script>
	import test from "../../components/test.vue"
	export default {
		data() {
			return {
				// title: 'Hello uni-app'
				// msg: 'ntuzy'
				msg: "lili",
				names: ['a','b','c','d'],
				currentIndex: 0,
				
			}
		},
		components: {
			test
		},
		onLoad() {
			// uni.$on("testEmit",(rel)=>{
			// 	console.log(rel)
			// })
		},
		methods: {
			setIndexItem(index) {
				this.currentIndex = index
			},
			toPath() {
				// uni.switchTab({
				// 	url: "../news/news"
				// })
				uni.navigateTo({
					url:"../one/one?name=ntuzy"
				})
			}
			// testEvent(rel) {
			// 	console.log(rel)
			// }
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.box111{
		width: 100px;
		height: 100px;
		background-color: pink;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
