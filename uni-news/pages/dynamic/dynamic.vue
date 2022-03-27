<template>
	<view>
		<!-- #ifdef MP-WEIXIN -->
	    <uni-stats-bar></uni-stats-bar>
		<view class="banner">
			
		</view>
	    <!-- #endif -->
	    </view>
</template>

<script>
	import uniStatusBar from '@/components/uni/uni-status-bar/uni-status-bar.vue'
	
	export default {
		components:{
			uniStatusBar
		},
		data() {
			return {
				
				user:{}
			}
		},
		onShow(){
			this.user = uni.getStorageSync('user');
			console.log(this.user)
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.banner {
		box-sizing: border-box;
		position: relative;
		width: 100%;
		height: 500rpx;
		background-color: #333;
	}
	
	.banner::before{
		content: '';
		position: absolute;
		top:0;
		left: 0;
		width: 100%;
		height: 450rpx;
		/*background-image: linear-gradient(45deg,#ff081,#6827b0);*/\
		/*background-image: var(--bgurl);*/
		/*background-repeat: no-repeat;*/
		border-radius: 0 0 50% 50%/0 0 100% 100%;
		transform: scaleX(1.5);
		z-index: 10;
	}
</style>
