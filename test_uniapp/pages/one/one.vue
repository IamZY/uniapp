<template>
	<view>
		<view>我是one页面</view>
		<button type="primary" @click="toPath">toIndex</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		// onLoad(option) {
		// 	console.log(option)
		// }
		methods: {
			toPath() {
				uni.navigateTo({
					url:"../index/index"
				})
			}
		}
	}
</script>

<style lang="scss">

</style>
