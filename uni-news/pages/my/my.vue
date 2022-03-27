<template>
	<view>	
	<!--未登录-->
		<template v-if="!loginStatus">
			<view>未登录</view>
			<image :src="avatar" class="size-100 rounded-circle"></image>
		</template>
		
		
		<!--登录-->
		<template v-else>
			
			<!--头像区域-->
			<view class="flex align-center p-2">
				<image :src="avatar" class="size-100 rounded-circle"></image>
			    <view class="flex-1 flex flex-column px-3">
					<text class="font-lg font-weight-bold text-muted">{{nickname}}</text>
					<view>
						<text class="mr-2">总帖数</text>
					    <text class="text-warning">{{posts}}</text>
						<text class="mx-2">今日发帖</text>
						<text class="text-warning">{{dynammics}}</text>
					</view>	
				</view>
				<text class="iconfont icon-jinru"></text>
			</view>
			
			<!--数据区域-->
			<view class="flex align-center px-2 py-3">
				<view class="flex flex-column flex-1 align-center justify-center">
					<text class="text-pink mb-1">{{posts}}</text>
					<text class="font-sm text-muted">帖子</text>
				</view>
				<view class="flex flex-column flex-1 align-center justify-center">
					<text class="text-pink mb-1">{{dynammics}}</text>
					<text class="font-sm text-muted">动态</text>
				</view>
				<view class="flex flex-column flex-1 align-center justify-center">
					<text class="text-pink mb-1">{{comment}}</text>
					<text class="font-sm text-muted">评论</text>
				</view>
				<view class="flex flex-column flex-1 align-center justify-center">
					<text class="text-pink mb-1">{{fans}}</text>
					<text class="font-sm text-muted">粉丝</text>
				</view>
			</view>
			
			<!--banner区域-->
			<view class="p-2">
				<image src="../../static/img/banner.png" mode="aspectFill" class="w-100"></image>
			</view>
			
			
			<!--列表区域-->
			
				<uni-list-item showExtraIcon title="浏览历史">
					<text slot="icon" class="iconfont icon-liulan">
					</text>
				</uni-list-item>
				
				<uni-list-item showExtraIcon title="会员vip">
					<text slot="icon" class="iconfont icon-huiyuanvip">
					</text>
				</uni-list-item>
				
				<uni-list-item showExtraIcon title="帖子审核">
					<text slot="icon" class="iconfont icon-keyboard">	
					</text>
				</uni-list-item>

		</template>
	</view>
</template>

<script>
	import uniListItem from '@/components/uni/uni-list-item/uni-list-item.vue';
	
	export default {
		components: {
			uniListItem
		},
		
		data() {
			return {
				loginStatus: true,
				nickname: '王秉谕',
				posts: 20,
				dynammics:12,
				comment:180,
				fans:333
			}
		},
		computed:{
			avatar(){
				return this.loginStatus === true ? '/static/img/me.jpg' : '/static/img/nologin.jpeg'
			}
		},
		onNavigationBarButtonTap() {
			uni.showToast({
				title:'点击', 
				duration: 2000
			})
		},
		methods: {

		}
	}
</script>

<style>

</style>
