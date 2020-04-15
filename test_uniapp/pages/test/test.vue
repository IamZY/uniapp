<template>
	<view>
		<!-- <view class="box1"></view>
		<view class="box2"></view> -->
		
		
		<view class="ld">
			<view class="left">
				<view 
					v-for="(item,index) in list" :key="index" @click="setId(index)" 
					:class="{active:index === currnetNum}">
					{{item.titile}}
				</view>
			</view>
			<view class="right">
				<scroll-view :scroll-y="true" style="white-space: nowrap;height: 200px;" :scroll-into-view="clickId"
				:scroll-with-animation = "true"
				@scroll="scroll" @scrolltolower="scrolltolower">
					<view v-for="(item,index) in list" :key="index">
						<view class="title" :id="'po' + index">{{item.titile}}</view>
						<view v-for="(it,idx) in item.list" :key="idx">
							{{it}}
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		
		
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
				clickId: "",
				currnetNum: 0,
				tops: []
			}
		},
		onReady() {
			// this.i = [3,4,5,6]
			this.getNodesInfo(),
			this.testRequest()
		},
		methods: {
			setId(index) {
				this.clickId = "po" + index;
				this.currnetNum = index
			},
			scrolltolower() {
				setTimeout(()=>{
					this.currnetNum = 3
				},80)
			},
			scroll(e) {
				// console.log(this.i)
				//console.log(e.target.scrollTop)
				let scrollTop = e.target.scrollTop
				// console.log(this.topList.length)
				console.log(this.tops)
				for(let i = 0;i < this.topList.length;i++) {
					let h1 = this.topList[i]
					let h2 = this.topList[i + 1]
					if(scrollTop >= h1 && scrollTop < h2) {
						this.currnetNum = i;
					}
				}
			},
			getNodesInfo() {
				const query = uni.createSelectorQuery().in(this)
				query.selectAll('.title').boundingClientRect().exec(function(data){
					// console.log(data)
					let nodes = data[0]
					let rel = []
					nodes.map(item=>{
						// console.log(item)
						rel.push(item.top)
					})
					// console.log(rel)
					this.tops = rel
					console.log(this.tops)
				})
			},
			testRequest() {
				uni.request({
				    url: 'https://bird.ioliu.cn/weather', //仅为示例，并非真实接口地址。
				    data: {
				        city: '北京'
				    },
				    success: (res) => {
				        console.log(res.data);
				        this.text = 'request success';
				    }
				})
			}
		}
	}
</script>

<style lang="scss">
.box1 {
	width: 100px;
	height: 100px;
	background: red;
}
.box2 {
	width: 100rpx;
	height: 100rpx;
	background: yellow;
}
.ld{
	display: flex;
	.left {
		width: 100px;
		border: 1px solid red;
		
	}
	.right {
		flex: 1;
		border:1px solid red;
		.title{
			font-size: 20px;
			font-weight: bold;
			background: pink;
		}
	}
}

.active {
	background: red;
}

</style>
