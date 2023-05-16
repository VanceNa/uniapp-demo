<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<button @click="add">添加</button>
	</view>
</template>

<script>
	const cloudObj1 = uniCloud.importObject("cloudObj")
	const db = uniCloud.database()
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {
			// cloudObj1.get().then((res) => {
			// 	console.log(res)
			// })
			db.collection("article").get().then((res)=>{
				console.log(res)
			})
		},
		methods: {
			add() {
				db.collection("cloudDemo").add({
					"title":"111112222"
				}).then((res)=>{
					console.log(res)
				})
				// let params = {
				// 	title: "澹台烬玲娜贝儿CP名",
				// 	author: "吃瓜姐妹",
				// 	content: "罗云熙，白鹿《长月烬明》昨日云合正片播放量市场占比率20.8%，不仅稳居第一，突破自身单日播放量新高。"
				// }
				// cloudObj1.add(params).then((res)=>{
				// 	console.log(res)
				// })

				}
			}
		}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
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