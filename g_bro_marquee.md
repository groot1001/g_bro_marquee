# 功能简介
1. 文字左右跑马灯
2. 文字上下滚栏
3. 左右滚动区域(自定义内容)
4. 上下滚动区域(自定义内容)
5. 样式自定义
6. 多端使用

## options参数说明

|参数|说明|类型|默认值|可选值|注意项|
|--	|--	|--	|--	|--|--|
|broadcastType|滚动类型|String|text|mould/text|无|
|direction|滚动方向|String|left|top/bottom/left/right|无|
|view_height|滚动区域可视高度|Number|400|--|单位:rpx; direction：left和right且broadcastType为"text"情况下不可用|
|broadcastStyle|滚动区域样式|Object|{speed: 30,font_size: "28",text_color: "#333",back_color: "red",}|--|mould模式下根据需求只传：{speed：***}即可|
|broadcastData|文字滚动数据|Array|--|--|text模式下可用|
|broadcastIconIsDisplay|文字滚动图标是否显示|Boolean|false|true/false|text模式下方向为left/right可用|
|broadcast_tit|文字滚动标题|String|今日热点|--|text模式下方向为left/right可用|
|touchEvent|指尖触摸暂停动画|Boolean|false|true/false|--|


|参数|说明|
|--	|--	|
|broadcastStyle.speed|mould模式下speed为每秒走N像素；text模式下speed为每秒走N 个字|

## 使用方式
#文字广播跑马灯类型(left/right)：
js:
``` javascript
    <script>
    	import gbroMarquee from '../../components/GBroMarquee/marquee.vue'
    	export default {
    		data() {
    			return {
    				broadcastData: ['秒秒天天答复是短发分公司噶阿飞嘎斯在', '分分答复是短发分公司噶阿飞嘎斯在', '时时答复是短发分公司噶阿飞嘎斯在', '天天答复是短发分公司噶阿飞嘎斯在',
    					'月月答复是短发分公司噶阿飞嘎斯在', '年年答复是短发分公司噶阿飞嘎斯在'
    				],
    				broadcastStyle: {
    					speed: 3, //每秒3个字
    					font_size: "32", //字体大小(rpx)
    					text_color: "#333", //字体颜色
    					back_color: "red", //背景色
    				},
    
    			}
    		},
    		components: {
    			gbroMarquee
    		},
    	}
    </script>
```

html:(为了兼容小程序在gbro-marquee 标签上加上style="width: 100%")
``` html
    <template>
    	<view class="content">
    		<gbro-marquee broadcastType='text'   direction="left"
    		 :broadcastIconIsDisplay="true" :broadcastData='broadcastData' :broadcastStyle='broadcastStyle' style="width: 100%">
    		</gbro-marquee>
    	</view>
    </template>
```

#文字上下滚动类型(top/bottom)：
js:
``` javascript
    <script>
    	import gbroMarquee from '../../components/GBroMarquee/marquee.vue'
    	export default {
    		data() {
    			return {
    				broadcastData: ['秒秒天天答复是短发分公司噶阿飞嘎斯在', '分分答复是短发分公司噶阿飞嘎斯在', '时时答复是短发分公司噶阿飞嘎斯在', '天天答复是短发分公司噶阿飞嘎斯在',
    					'月月答复是短发分公司噶阿飞嘎斯在', '年年答复是短发分公司噶阿飞嘎斯在'
    				],
    				broadcastStyle: {
    					speed: 30, //每秒30px
    					font_size: "32", //字体大小(rpx)
    					text_color: "#333", //字体颜色
    					back_color: "red", //背景色
    				},
    
    			}
    		},
    		components: {
    			gbroMarquee
    		},
    	}
    </script>
```

html:(为了兼容小程序在gbro-marquee 标签上加上style="width: 100%")
``` html
    <template>
    	<view class="content">
    		<gbro-marquee broadcastType='text'   direction="top"
    		  :broadcastData='broadcastData' :broadcastStyle='broadcastStyle' style="width: 100%">
    		</gbro-marquee>
    	</view>
    </template>
```

#mould类型(left/right/top/bottom)：
js:
``` javascript
    <script>
    	import gbroMarquee from '../../components/GBroMarquee/marquee.vue'
    	export default {
    		data() {
    			return {
    				broadcastStyle: {
    					speed: 100, //每秒100px
    				},
					imgdata:['https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2599053290,1467680116&fm=11&gp=0.jpg','https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=572690740,3931194854&fm=11&gp=0.jpg','https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=21157214,1564611442&fm=26&gp=0.jpg']
    
    			}
    		},
    		components: {
    			gbroMarquee
    		},
    	}
    </script>
```

html:(为了兼容小程序在gbro-marquee 标签上加上style="width: 100%")
``` html
    <template>
    	<view class="content">
    		<gbro-marquee broadcastType='mould'   direction="left" :broadcastStyle='broadcastStyle' style="width: 100%">
    		    <view  v-for="(item,ind) in imgdata" :key="ind" class="img_item2">
    		    	<image :src="item" mode=""></image>
    		    </view> 
			</gbro-marquee>
    	</view>
    </template>
	
	<style>
	.img_item2,.img_item2 image{
		/* float: left; */
		width: 320rpx;
		height: 220rpx;
		margin: 20rpx;
	}
	</style>
```


# 注意：该插件目前测试有App/Apk端、H5端和微信小程序端，其他端暂时未测试