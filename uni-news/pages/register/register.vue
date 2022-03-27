<template>
	<view>
		<!-- #ifndef MP-WEIXIN -->
		<uni-status-bar></uni-status-bar>
		<view @tap="back"
		class="iconfont icon-guanbi flex align-center justify-center font-lg size-100">
		</view>
	    <!-- #endif -->
	
		<template>

			<view>
				<view class="text-center" style="padding-top: 90rpx; padding-bottom: 90rpx;">
					<text class="h2 text-body">注册</text>
				</view>
				<view class="flex md-2 px-2 ">
					<input type="text" v-model="name" placeholder="用户名" class="border-bottmom p-2 flex-1" style="outline-color: #C8C7CC; margin: 7px auto; outline-style:auto;">
				</view>
				<view class="flex md-2 px-2 ">
					<input type="text" v-model="phone" placeholder="手机号" class="border-bottmom p-2 flex-1" style="outline-color: #C8C7CC; margin: 7px auto; outline-style:auto;">
				</view>
				<view class="flex md-2 px-2 ">
					<input type="text" v-model="email" placeholder="邮箱地址" class="border-bottmom p-2 flex-1" style="outline-color: #C8C7CC; margin: 7px auto; outline-style:auto;">
				</view>
				<view class="flex md-2 px-2 ">
					<input type="text" v-model="password" placeholder="输入密码" class="border-bottmom p-2 flex-1" style="outline-color: #C8C7CC; margin: 7px auto; outline-style:auto;">
				</view>
				<view class="flex md-2 px-2">
					<input type="text" v-model="pwdConfirm" placeholder="确认密码" class="border-bottmom p-2 flex-1 " style="outline-color: #C8C7CC; margin: 7px auto; outline-style:auto;">
				</view>
			</view>
			<view class="p-2">
				<button class="rounded-circle text-white shadow " style="background-color: #FC5C82;" @tap="register()">注册</button>
			</view>
			
			<view class="text-center text-muted mt-3">
				<text class="text-primary" @tap="back()">已有帐号</text>
				<input type="checkbox">
			</view>
			
			<!--图标区域-->
			<view class="text-center" >
				<uni-list-item style="padding-right: 70rpx;">
					<text slot="icon" class="iconfont icon-weixin text-white rounded-circle " style="background-color: #4CD964;">	
				    </text>
			    </uni-list-item>
				<uni-list-item style="padding-right: 70rpx;">
					<text slot="icon" class="iconfont icon-QQ text-white rounded-circle" style="background-color: #007BFF;">	
				    </text>
				</uni-list-item>
				<uni-list-item>
					<text slot="icon" class="iconfont icon-xinlangweibo text-white rounded-circle" style="background-color: #FFC107;">	
				    </text>
				</uni-list-item>
			</view>


		</template>
		
		
		

	</view>
</template>

<script>
	import uniStatusBar from '@/components/uni/uni-status-bar/uni-status-bar.vue';
	export default {
		components:{
			uniStatusBar

		},
		data() {
			return {
				phone:'',
				name:'',
				password:'',
				pwdConfirm:'',
				email:'',
				limitTime:0
			}
		},
		methods: {
			back() {
				uni.showToast({
					title:"返回",
					duration:2000
				})
			},
				register(){
					let data={
						username:'wby',
						password:'123123'
					}
					const url = "http://106.14.169.149:8071/login";
					url.request({
						uyrl: url,
						method: 'POST',
						data: data,
					}).then((res)=>{
						console.log(res)
						console.log(res[1].data.data.nickname)

					})
				}
		}
	}
</script>

<style>

</style>


