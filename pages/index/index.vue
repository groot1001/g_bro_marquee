<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<gbro-marquee  broadcastType='text' @changeEvent='testClick' direction="left" :viewHeight="200"
		 :broadcastIconIsDisplay="!true" :touchEvent="true" :broadcastData='broadcastData' :broadcastStyle='broadcastStyle'
		 style="width: 100%"> -->
		
			<view v-for="(item,ind) in imgdata" :key="ind" class="img_item2">
				<image :src="item" mode=""></image>
			</view>
		</gbro-marquee>
	</view>
</template>

<script>
	import gbroMarquee from '../../components/GBroMarquee/marquee.vue'
	export default {
		data() {
			return {
				title: 'Hello',
				broadcastData: ['秒秒天天答复是短发分公司噶阿飞嘎斯在','天天答复是短发分公司噶阿飞嘎斯在',
					'月月答复是短发分公司噶阿飞嘎斯在', '年年答复是短发分公司噶阿飞嘎斯在'
				],
				broadcastStyle: {
					speed: 3, //每秒3个字
					font_size: "32", //字体大小(rpx)
					text_color: "#333", //字体颜色
					back_color: "red", //背景色

				},
				imgdata: ['https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=2599053290,1467680116&fm=11&gp=0.jpg',
					'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=572690740,3931194854&fm=11&gp=0.jpg',
					'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=21157214,1564611442&fm=26&gp=0.jpg'
				]


			}
		},
		onLoad() {
			let that = this;
			setTimeout(() => {
				that.broadcastData = ['秒秒天天答复是短发分公司噶阿飞嘎斯在',
					'月月答复是短发分公司噶阿飞嘎斯在', '年年答复是短发分公司噶阿飞嘎斯在'
				]
			}, 300)
		},
		components: {
			gbroMarquee
		},
		methods: {
			testClick(e) {
				console.log(e)
			}
		}
	}
</script>

<style>
	.img_item2,
	.img_item2 image {
		/* float: left; */
		width: 320rpx;
		height: 220rpx;
		margin: 20rpx;
	}

	.img_item {
		width: 90%;
		margin: 20rpx auto;
	}

	.img_item image {
		width: 100%;
		height: 300rpx;
	}

	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		overflow: hidden;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
