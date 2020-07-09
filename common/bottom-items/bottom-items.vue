<template>
	<view :class="flag?'change-color':'bottomContent'">
		<view class="titleContent" >
			
			<view v-for="v in titleList" :key="v.id"
			:class="v.id==titleId?'  titlePadding titleItem  ':' titlePadding '" 
			 >
			  
			 <view 
			 
			 class="font-color"  
			  @tap="getItems(v.id)">{{v.name}}</view>
			
			</view>
		</view>
		<view class="search">
			<input type="text" value="" class="iconfont " :placeholder="icon" />
		</view>
		
		<!-- 相关数据 -->
		<view v-if="titleId==1"  class="datas">
			<Bottomdata :dataList="dataList.Favorites" :flag="flag"></Bottomdata>
			
		</view>
		<view v-if="titleId==2" class="datas" >
			<Bottomdata :dataList="dataList.USDT" :flag="flag"></Bottomdata>
			
			
			
			
		</view>
		<view v-if="titleId==3" class="datas"  >
			<Bottomdata :dataList="dataList.BTC" :flag="flag" ></Bottomdata>
			
		</view>
					
		
		
	</view>
</template>

<script>
	import Bottomdata from'../bottom-data/bottom-data.vue'
	
	
	export default{
		components:{
			Bottomdata
		},
		props:{
			flag:Boolean
		},
		
		data(){
			return{
				
				dataList:{
					"Favorites":[],
					"USDT":[
						{id:1,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.89%"},
						{id:2,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"-3.89%"},
						{id:3,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+4.89%"},
						{id:4,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.89%"},
						{id:5,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.79%"},
						{id:6,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+5.79%"},
						{id:7,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.79%"},
						{id:8,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.79%"},
						{id:9,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.79%"},
						{id:10,name:"BCH/USD",price:'0.0069',discount:'6.45',add:"-3.79%"},
						
						
						],
					"BTC":[
						{id:1,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.89%"},
						{id:2,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"-3.89%"},
						{id:3,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+4.89%"},
						{id:4,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+3.89%"},
						{id:5,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"-3.89%"},
						{id:6,name:"ETC/BTC",price:'0.0069',discount:'6.45',add:"+4.89%"},
					],
					
				},
				titleId:1,
				icon:"\ue633SearchIcon",
				
				
				
				
				titleList:[
					{id:1,name:"Favorites"},
					{id:2,name:"USDT"},
					{id:3,name:"BTC"}
					
				]
			}
		},
		methods:{
			getItems(id){
				this.titleId=id
				
			}
		}
	}
</script>

<style>
	.datas{
		flex:1
	}
	.bottomContent{
		background-color: #FFFFFF;
		display: flex;
		flex-direction: column;
		
		
		
	}
	.titleContent{
		display: flex;
		justify-content: space-around;
		align-items: center;
		
		
	}
	.titleItem{
		border-bottom: solid 2rpx #24a0f5;
		
		
	}
	.titlePadding{
		padding:10rpx 0;
		color: rgb(29, 38, 53);
		font-size:28rpx;
		
	}
	.search{
		display: flex;
		justify-content: center;
		margin:30rpx;
		height: 60rpx;
	}
	input{
		width: 90%;
		outline: none;
		
		height: 100%;
		border: solid 1rpx #000000;
		
	}
	.datas{
	
		
	}
	
	
</style>
