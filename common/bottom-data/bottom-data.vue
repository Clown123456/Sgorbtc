<template>
	<view class="dataContents">
		<view v-if='dataList.length<1'class="No" >
			<view :class=" flag? 'dark-color noData':'noData'">
				<i class="iconfont icon-shenqing"></i>
				<view class="ends">No Datas</view>
			</view>
			
		</view>
		<view v-else>
			<view class="topContents" >
				<block v-for="item in topList " :key='item.id'>
					<view class="topContent">
						<view class="leftIcon main-font-color">{{item.name}}</view>
						<view class="icons">
							<i class="iconfont icon-shangjiantou" ></i>
							<i class="iconfont icon-xiajiantou" ></i>
						</view>
					</view>
				</block>
				
			</view>
			<!-- 数据，封装 -->
			<block v-for="v in dataList " :key="v.id" >
				<view class="dataContent">
					<view class="dataItem">
						<i class="iconfont icon-ai64 icon-color"></i>
						<text :class="flag?'commot-font dark-color':'main-font-color'">{{v.name}}</text>
					</view>
					<view class="centerData">
						<text :class="flag?'commot-font dark-color':'main-font-color' ">{{v.price}}</text>
						<text class="grey-font-color" >≈${{v.discount}}</text>
					</view>
					<view :class="v.add.substring(0,1)=='+'?'rightData':'rightDatas'"
					style="color: #FFFFFF;font-size: 28rpx;"
					>{{v.add}}</view>
					
					
				</view>
				
			</block>
			
		</view>
	</view>
	
</template>

<script>
	export default{
		props:{
			dataList:Array,
			flag:Boolean
		},
		data(){
			return{
				topList:[
					{id:1,name:"Markets"},
					{id:2,name:"Last Price"},
					{id:3,name:"Change"}
				],
				
			}
		}
	}
	
</script>

<style>
	
	.No{
		height:240px;
	}
	
	
	
	
	.noData{
		display: flex;
		justify-content: center;
		align-items: center;
		
		padding-top: 200rpx;
	}
	.topContents{
		display: flex;
		justify-content: space-between;
		border-bottom: solid 2rpx #000000;
		padding: 20rpx 0;
	}
	.topContent{
		display: flex;
		/* padding: 0 20rpx; */
		margin: 20rpx 10rpx;
	}
	.leftIcon{
		margin-right: 20rpx;
	}
	.icons{
		display: flex;
		flex-direction: column;
		justify-content: center;
		line-height: 20rpx;
	}
	/* 具体数据 */
	.commot-font{
		font-size: 28rpx;
	}
	.dataContent{
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 20rpx ;
		margin-top: 20rpx 0;
		
	}
	.dataItem{
		padding: 20rpx 0;
		height: 76rpx;
	}
	.centerData{
		display: flex;
		flex-direction: column;
		align-items: flex-end;
	}
	/* 正增长颜色 */
	.rightData{
		height: 76rpx;
		width: 128rpx;
		background-color: #03ad8f;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 10rpx;
		
	}
	/* 负增长颜色 */
	.rightDatas{
		height: 76rpx;
		width: 128rpx;
		background-color: red;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 10rpx;
		
	}
	
</style>
