<template>
	
		<view class="content" >
			 <view class="status_bar">
			       <!-- 这里是状态栏 -->
			   </view>   
			<!-- 头部 -->
			<view :class="flag?'change-color header' :'header'">
				<image :src="flag?'../../static/logo1.png':'../../static/logo.png'" class="logoImgContent" ></image>
				<view>
					<i :class="flag?'iconfont icon-yejianmoshishenyemoshiyueliang':'iconfont icon-taiyang'"  ></i>
		
					<switch size="20" 
					  
					 @change="changes"
					 style="transform:scale(0.4)"
					  ></switch>
				</view>
				<view :class="flag? 'dark-color':'main-font-color'">
					Log In/Sign Up  
					<i class="iconfont icon-webicon03" style="margin-left: 15rpx;" @tap="shows()" ></i>
					
				</view>
			</view>
			<!-- swiper -->
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item >
					<image src="../../static/img/s1.png" mode="" class="swipeImg"></image>
				</swiper-item>
				<swiper-item >
					<image src="../../static/img/s2.jpg" class="swipeImg" mode=""></image>
				</swiper-item>
				<swiper-item>
					<image src="../../static/img/s3.jpg"  class="swipeImg" mode=""></image>
				</swiper-item>	
			</swiper>
			<!-- 这是横向滑动区域 -->
			<BlockSwip :flag="flag"></BlockSwip>
			<BottomItems :flag="flag"></BottomItems>
			
			<!-- 点击右上角，出现popup -->
			<u-popup 
			
			 ref="popup" 
			 mode="right"
			  style="top: 150rpx;" 
			  :mask='maskFlag'
			   :maskCloseAble='maskFlag'
			   width="100%"
				
			   >
			   <view :class="flag?'change-color maskContent':'maskContent'">
				   <view class="login-sign">
				   			   <view :class="flag?'dark-color comlo-si':'comlo-si'"  style="border: solid 2rpx #007AFF;">Log In</view>
				   			   <view class="comlo-si" style="background-color:  #24a0f5;color: #FFFFFF;">Sign Up</view>
				   			   
				   </view>
				   <view>
				   			   <block v-for="v in maskData" :key='v.id'>
				   				   <view class="userItems">
				   					   <i :class="v.iconName"></i>
				   					   <view class="myName font-color">{{v.name}}</view>  
				   				   </view>
				   				   
				   			   </block>
				   			   
				   </view>
			   </view>
			   </u-popup>
			
		
			
			
			
			
			
			
			
			
			
		</view>
	
	
</template>

<script>
	import BlockSwip from '@/common/blockSwip/blockSwip.vue'
	import BottomItems from '@/common/bottom-items/bottom-items.vue'
	import UniPopup from '../../uni-popup/uni-popup.vue'
	
	
	export default {
		components:{
			BlockSwip,
			BottomItems,
			UniPopup
			
		},
		data() {
			return {
				// 显示popup
				flag:false,
				//控制蒙版的显示和是否能够点击,
				maskFlag:false,
				//弹出层是否收起
				maskShow:false,
				//蒙版数据
				maskData:[
					{id:1,iconName:'iconfont  font-color  icon-jiaoyi',name:'Currenty trading'},
					{id:2,iconName:' iconfont  font-color icon-zhanghao',name:'My account'},
					{id:3,iconName:' iconfont  font-color icon-ding_huabanfuben',name:'Purchase order'},
					{id:4,iconName:' iconfont  font-color icon-xiaoxi3',name:'Message'},
					{id:5,iconName:' iconfont  font-color icon-shezhi',name:'Language'},
					{id:6,iconName:' iconfont  font-color icon-chenggong',name:'Start the subscription'},
					{id:7,iconName:' iconfont  font-color icon-shenqing',name:'Issue new currency'},
					{id:8,iconName:' iconfont  font-color icon-qianbao',name:' Wallet assets'}
				],
				
				
				
			}
		},
		onLoad() {
			

		},
		methods: {
			// switch 状态改变的时候
			changes(e){
				// console.log(e.target.value)
				this.flag=e.target.value
				
			},
			// 展示抽屉
			shows(){
				console.log(this.maskShow)
				this.maskShow=!this.maskShow
				if(this.maskShow){
					this.$refs.popup.open()
				}else{
					this.$refs.popup.close()
				}
				
			}

		},
		
	}
</script>

<style>
	
	
	
	
	
	.content{
		background-color: rgb(237, 237, 237);
		/* position: fixed;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
		height: 100%;
		 */
		
		
	}
	.status_bar {
	      height: var(--status-bar-height);
	      width: 100%;
	  }
	.header{
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		height:120rpx ;
		
	
		
		
	}
	.logoImgContent{
		height:40px ;
		width: 100px;
		
	}
	
	.swipeImg{
		width:750rpx;
		height: 350rpx;
	}
	/* 蒙版 */
	/deep/.u-mask[data-v-1c661818] {
		  
		     position: relative;
		         height: 0;
				 width: 0;
	}
	.uni-scroll-view-content{
		overflow-y: hidden;
	}
	
	.maskContent{
		padding: 0 40rpx;
			height: 100vh;
	}
	.login-sign{
		display: flex;
		justify-content: space-between;
		padding: 40rpx 0;
	
	}
	.comlo-si{
		
		padding: 20rpx 100rpx;
		font-size: 26rpx;
	}
	.userItems{
		display: flex;
		align-items: center;
		padding: 30rpx 0;
	}
	.myName{
		margin-left: 20rpx;
	}
	
	
</style>
