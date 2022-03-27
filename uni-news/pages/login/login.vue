<template>
	<view >
		<!-- #ifndef MP-WEIXIN -->
		<uni-status-bar></uni-status-bar>
		<view @tap="back"
		class="iconfont icon-guanbi flex align-center justify-center font-lg size-100">
			
		</view>
	    <!-- #endif -->
	
		<template v-if="choice">
			<!--账号密码登录-->
			<view>
				<view class="text-center" style="padding-top: 90rpx; padding-bottom: 90rpx;">
					<text class="h3 text-body">账号密码登录</text>
				</view>
				<view class="flex md-2 px-2 ">
					<input type="text" v-model="phone" placeholder="手机号" class="border-bottmom p-2 flex-1">
				</view>
				<view class="flex md-2 px-2">
					<input type="text" v-model="password" placeholder="请输入密码" class="border-bottmom p-2 flex-1 ">
				    <view class="font-sm text-muter px-3 flex align-center">
						忘记密码？
					</view>
				</view>
			</view>
			<view class="p-2">
				<button class="rounded-circle text-white shadow " style="background-color: #FC5C82;" @tap="login()">登录</button>
			</view>
			
			<view class="text-center mt-3 text-primary font-sm">
				<text @tap="choice=!choice">验证码登录</text>
				<text>|</text>
				<text>登录遇到问题</text>
			</view>
			
			<view class="text-center text-muted mt-3">
				注册即代表同意
				<text class="text-primary">《xxx协议》</text>
				<input type="checkbox">
			</view>
			
			<!--图标区域-->
			<view class="text-center">
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
		
		
		
		<template v-else>
			<!--手机验证码登录-->
			<view>
				<view class="text-center" style="padding-top: 90rpx; padding-bottom: 90rpx;">
					<text class="h3 text-body">手机验证码登录</text>
				</view>
				<view class="flex md-2 px-2 ">
					<view class="border-right fonr px-2 flex align-center">+86</view>
					<input type="text" v-model="phone" placeholder="手机号" class="border-bottmom p-2 flex-1">
				</view>
				<view class="flex md-2 px-2">
					<input type="text" v-model="verifyCode" placeholder="请输入验证码" class="border-bottmom p-2 flex-1 ">
				    <view @tap="getCode":class="limitTime >0 ? 'bg-pink-dsiabled': 'bg-pink'"
					 class="font-sm text-muter px-3 flex align-center bg-pink r rounded text-white">
						获取验证码
					</view>
				</view>
			</view>
			<view class="p-2">
				<button class="rounded-circle text-white shadow " disabled >
					登录</button>
			</view>
			<view class="text-center mt-3 text-primary font-sm">
				<text @tap="choice=!choice">账号密码登录</text>
				<text>|</text>
				<text>登录遇到问题</text>
			</view>
			<view class="text-center text-muted mt-3">
				注册即代表同意
				<text class="text-primary">《xxx协议》</text>
				<input type="checkbox">
			</view>
			
			<!--图标区域-->
			<view class="text-center">
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
				</uni-list-item>y
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
				choice:false,
				phone:'',
				password:'',
				verifyCode:'',
				limitTime:0
			}
		},
		methods: {
			gotoPage() {
				this.$router.push({
					path:''
				})
			},
			back() {
				uni.showToast({
					title:"返回",
					duration:2000
				})
			},
			getCode() {
				//防止重复获取验证码
				if(this.limitTime >0){
					return;
				}
				//验证手机号-没通过
				if(this.validate()){
					return;
				}
				//验证手机号-通过
				this.limitTime = 5;
				let timer = setInterval(()=>{
					if(this.limitTime >=1){
						this.limitTime--;
					}else{
						this.limitTime = 0;
						clearInterval(timer);
					}
				},1000)
			},
			validate() {
			      //手机号正则
			      var mPattern = /^1[34578]\d{9}$/;
			      if (!mPattern.test(this.phone)) {
			        uni.showToast({
			          title: '手机号格式不正确',
			          icon: 'none'
			        });
			        return false;
			      }
			      // ...更多验证
			      return true;
			    },
				login(){
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
