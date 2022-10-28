<template>
	<view>
		<text>控制台</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			navgateTo(){
			    console.log(11)
			  uni.switchTab({
			  	url:"./collection"
			  })
			}
		}
	}
</script>

<style>

</style>
