<template>
	<view>
		<uni-list-item title="账号与安全">
		</uni-list-item>
		
		<uni-list-item title="资料编辑">
		</uni-list-item>
		
		<uni-list-item title="清理缓存">
		</uni-list-item>
		
		<uni-list-item title="意见反馈">
		</uni-list-item>
		
		<uni-list-item title="关于社区">
		</uni-list-item>
		
		<view class="p-2">
			<button class="rounded-circle text-white shadow " style="background-color: #FC5C82;">退出登录</button>
		</view>
	</view>
</template>

<script>
	import uniListItem from '@/components/uni/uni-list-item/uni-list-item.vue'
	export default {
		components:{
			uniListItem
		},
		data() {
			return {
				currentSize: 10010 //缓存大小
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
