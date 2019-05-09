<template>
	 <view>
		 <block v-for="(item,index) in news" :key="index">
		 <navigator class="news-list" url="../info/info" >
			 <image src="../../static/image/index.png" mode="widthFix"></image>
			 <view class="news-title">{{item.title}}</view>
		 </navigator>
		 </block>
	 </view>
	
</template>

<script>
	var _self;
	export default {
		data: {
		
		},
		onLoad:function (e) {
			_self=this;
			_self.getNews();
	},
	methods:{
		getNews:function(){
			uni.request({
				url:"https://wxa.sytours.com/Citylist/GetArticleByKeyword?kw=常州&page=1",
				success:function (res) {
					console.log(res);
					_self.news=res.data;
					console.log(res.data);
				} 
									
			})
		}
	},

	
	}
</script>

<style> 
view{
	width: 100%;
}
  .news-list{
	display: flex;
	width: 94%;
	padding: 10upx 3%;
	flex-wrap: nowrap;
	margin: 12upx 0;
  }
  .news-list image{
	 width: 200upx; 
	 margin-right: 12upx;
	 flex-shrink: 0;
  }
   .news-title{
	   width: 100%;
	   
	   height: auto;
	   font-size: 28upx;
   }
  
</style>
