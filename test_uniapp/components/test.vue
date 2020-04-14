<template>
	<view>
		<text>我是text组件{{msg1}}</text>
		<button type="primary" @click="test">event</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		props: ["msg1"],
		methods: {
			test() {
				// this.$emit("testShowName",{name:"ntuzy"})
				uni.$emit("testEmit",{name:"zy"})
			}
		}
	}
</script>

<style lang="scss">

</style>
