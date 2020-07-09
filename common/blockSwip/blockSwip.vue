<template>
	<view >
		
			<scroll-view scroll-x="true" show-scrollbar="false">
				<view class="blockSwipContent" >
					<block v-for="v in blockList ":key="v.id">
						<view :class="flag?'change-color blockSwip':'blockSwip blockSwips'">
							<text >
								<text  :class=" flag? 'dark-color bolckFir':'main-font-color bolckFir'" >{{v.name}}</text>
								<text class="special-font-color" >{{v.add}}</text>
							</text>
							<text class="font-color">{{v.num1}}</text>
							<text class="font-color">{{v.num2}}</text>
							<text class="font-color">{{v.num3}}</text>	
						</view>
					</block>
					
					
					
					
				</view>
				
				
							
			</scroll-view>
			
			
				
			
			
			
		
	</view>	
		
		
</template>

<script>
	export default{
		props:{
			flag:Boolean
		},
		data(){
			return{
				blockList:[
					{id:1,name:"LTC/USDT",add:"+2.23%",num1:'44.56',num2:'24H vol',num3:'195424.1248'},
					{id:2,name:"ETC/USDT",add:"+2.23%",num1:'44.56',num2:'24H vol',num3:'195424.1248'},
					{id:3,name:"LTH/USTD",add:"+2.24%",num1:'44.58',num2:'23H vol',num3:'195424.1248'},
					{id:4,name:"EOS/USDT",add:"+2.23%",num1:'46.56',num2:'24H vol',num3:'195424.1248'},
					{id:5,name:"TBIC/USDT",add:"+3.23%",num1:'48.56',num2:'24H vol',num3:'1954454.1248'},
					{id:6,name:"TBIC/USDT",add:"+3.23%",num1:'48.56',num2:'24H vol',num3:'1954454.1248'},
					{id:7,name:"TBIC/USDT",add:"+3.23%",num1:'48.56',num2:'24H vol',num3:'1954454.1248'},
					
				]
				
			}
		}
	}
</script>

<style>
	
	.blockSwip{
		width: 300rpx;
		height: 180rpx;
		
		margin: 10rpx;
		padding:10rpx ;
		display: flex;
		flex-direction: column;
	}
	.blockSwips{
		background-color: #FFFFFF;
	}
	.bolckFir{
		margin-right: 40rpx;
	}
	.blockSwipContent{
		display: flex;
		flex-wrap: nowrap;
	}
	
	
</style>
